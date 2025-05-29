```
CategoricalTabularPolicy
```

represents a stochastic policy sampling an action from a categorical distribution with weights given by a `ValuePolicy`

constructor:

`CategoricalTabularPolicy(mdp::Union{POMDP,MDP}; rng=Random.default_rng())`

# Fields

  * `stochastic::StochasticPolicy`
  * `value::ValuePolicy`
