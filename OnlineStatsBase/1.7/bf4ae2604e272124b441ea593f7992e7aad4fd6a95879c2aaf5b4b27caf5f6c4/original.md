```
ExponentialWeight(λ::Float64)
ExponentialWeight(lookback::Int)
```

Exponentially weighted observations.  Each weight is `λ = 2 / (lookback + 1)`.  

`ExponentialWeight` does not satisfy the usual assumption that `γ(1) == 1`.  Therefore, some statistics have an implicit starting value. 

```
# E.g. Mean has an implicit starting value of 0.
o = Mean(weight=ExponentialWeight(.1))
fit!(o, 10)
value(o) == 1
```

$γ(t) = λ$
