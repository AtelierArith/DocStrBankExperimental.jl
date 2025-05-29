```
State{T}
```

Memorise the (global) evolution of the bandit in the environment. This structure mostly contains information required by most bandit algorithms to decide their next step.

  * `round`: the number of rounds (time steps) the bandit has already played
  * `regret`: the total regret the bandit faced (i.e. how much more reward it would have got if it always played the optimum solution)
  * `reward`: the total reward the bandit managed to gather
  * `arm_counts`: the number of times each arm (and not each solution, which is a set of arms)  has been played. This information is used by most bandit algorithms
  * `arm_reward`: the total reward obtained by this arm
  * `arm_average_reward`: the average reward obtained by this arm. This information is used by most bandit algorithms
  * `policy_extension`: if a policy needs more information than this structure contains, it can store, in a key that uniquely identifies the policy, anything it might require
