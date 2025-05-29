```
DiscretePOMGBelief
```

A belief specified by a probability vector.

Normalization of `b` is assumed in some calculations (e.g. pdf), but it is only automatically enforced in `update(...)`, and a warning is given if normalized incorrectly in `DiscreteBelief(pomdp, b)`.

# Constructor

```
DiscretePOMGBelief(game::POMG, b::Vector{Float64}; check::Bool=true)
```

# Fields

  * `game` : the POMG problem
  * `state_list` : a vector of ordered states
  * `b` : the probability vector
