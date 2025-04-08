# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Xiaoying Yang

```
A total of three sampling stages are present in the model.

Stage one: This relates to the content from the blog post about supposing that exactly 10% of people at every event are infected. In the context of the code we are examining, the ’np.random.choice’ function is used to randomly choose 10% of the total population (who attended either the wedding or the brunch event) to be ‘’infected’.
Therefore, the sample size is 10% of the total population, and the sampling frame is the sum of the population who attended either the wedding or the brunch event. The distribution should be uniform, as everyone has the same probability of being infected.

Stage two: This relates to the content from the blog post about imperfect primary contact tracing, and an infection has an estimated chance of 20% to be traced. In the context of the code we are examining, the ’np.random.rand’ function is used to randomly choose 20% of the infected population as ‘successfully traced’, and 80% as ‘’not traced’.
The sample size is 20% of the infected population, and the sampling frame is the sum of the infected individuals. The distribution should be binomial, as each infected individual has 20% probability of being traced (success) and 80% probability of not being traced (failure).

Stage three: This relates to the content from the blog post about secondary contact tracing. If two infections are traced to the same event, then every person who attended that event would be tested, and all infections associated with that event would be identified. It used conditional section functions to filter those events where at least two infections are traced.
The sample size is the events where at least two infected people are traced. The sampling frame is all events that have traced infections. The distribution will be biased to the right (overestimate) toward larger events like weddings, as more infections will likely be traced, given that a larger group of people attend those events.


When the Python script is run, however, the code doesn’t seem to reproduce the graphs from the original blog post. The true proportion and the observed proportion from the code output agree more with each other, which is different from the blog post. By modifying the number of repetitions in the simulation to 100, the reproducibility of the results decreases more than that of 1000 repetitions. 
I insert a random seed before the def statement. It helps the model to select the exact same people at the three sampling stages, leading to a reproducible output.

```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `23:59 - 09/04/2025`
* The branch name for your repo should be: `assignment-1`
* What to submit for this assignment:
    * This markdown file (a1_sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `assignment-1`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via the help channel in Slack. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
