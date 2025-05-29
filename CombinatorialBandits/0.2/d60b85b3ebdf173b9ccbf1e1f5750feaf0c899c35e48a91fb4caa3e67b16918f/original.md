```
Trace{T}
```

Memorise all the details about the evolution of the bandit in the environment. This object can therefore become very heavy for long episodes.

The information is stored in several vectors, all of them having the same length equal to the number of rounds the bandit was used:

  * `states`: a list of states the bandit entered into over the episode
  * `arms`: a list of sets of arms that have been played over the episode
  * `reward`: a list of reward the policy received over the episode
  * `policy_details`: a list of policy-defined details over the episode (typically, computation times)
  * `time_choose_action`: a list of times (in milliseconds) to take a round decision over the episode
