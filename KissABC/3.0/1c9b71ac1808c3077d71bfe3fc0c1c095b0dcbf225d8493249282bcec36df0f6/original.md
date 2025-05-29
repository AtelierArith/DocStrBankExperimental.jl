```
ApproxPosterior(
    prior::Distribution,
    cost::Function,
    max_cost::Real
)
```

this function will return a type which can be used in the `sample` function as an ABC density, this type works by assuming uniformly distributed errors in [-ϵ,ϵ], ϵ is specified in the variable `max_cost`.
