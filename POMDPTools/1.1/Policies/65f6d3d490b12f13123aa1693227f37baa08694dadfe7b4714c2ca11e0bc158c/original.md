```
SoftmaxPolicy <: ExplorationPolicy
```

represents a softmax policy, sampling a random action according to a softmax function.  The softmax function converts the action values of the on policy into probabilities that are used for sampling.  A temperature parameter or function can be used to make the resulting distribution more or less wide.

# Constructor

`SoftmaxPolicy(problem, temperature::Union{Function, Float64}; rng=Random.default_rng())`

If a function is passed for `temperature`, `temperature(k)` is called to compute the value of the temperature when calling `action(exploration_policy, on_policy, k, s)`

# Fields

  * `temperature::Function`
  * `rng::AbstractRNG`
  * `actions::A` an indexable list of action
