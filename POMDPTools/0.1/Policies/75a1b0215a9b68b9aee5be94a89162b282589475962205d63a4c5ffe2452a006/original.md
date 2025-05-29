```
EpsGreedyPolicy <: ExplorationPolicy
```

represents an epsilon greedy policy, sampling a random action with a probability `eps` or returning an action from a given policy otherwise. The evolution of epsilon can be controlled using a schedule. This feature is useful for using those policies in reinforcement learning algorithms. 

# Constructor:

`EpsGreedyPolicy(problem::Union{MDP, POMDP}, eps::Union{Function, Float64}; rng=Random.default_rng(), schedule=ConstantSchedule)`

If a function is passed for `eps`, `eps(k)` is called to compute the value of epsilon when calling `action(exploration_policy, on_policy, k, s)`.

# Fields

  * `eps::Function`
  * `rng::AbstractRNG`
  * `m::M` POMDPs or MDPs problem
