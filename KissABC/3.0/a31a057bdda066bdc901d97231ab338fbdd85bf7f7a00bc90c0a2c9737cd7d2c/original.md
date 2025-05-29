```
ApproxKernelizedPosterior(
    prior::Distribution,
    cost::Function,
    target_average_cost::Real
)
```

this function will return a type which can be used in the `sample` function as an ABC density, this type works by assuming Gaussianly distributed errors 𝒩(0,ϵ), ϵ is specified in the variable `target_average_cost`.
