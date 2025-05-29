```
CombinatorialInstance{T}
```

A combinatorial instance, also called an environment in reinforcement learning. An instance is the combination of a combinatorial structure (i.e. what the bandit is allowed to make in the environment) and of the statistical properties of the arms (i.e. what reward the bandit gets).

Two properties are mandatory:

  * `n_arms`: the number of arms that are available in the instance (i.e. the dimension of the problem)
  * `optimal_average_reward`: the best reward that can be obtained at any round, in expectation
