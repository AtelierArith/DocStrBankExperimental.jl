```
getbasemeasure(::Type{<:Distribution}, [ conditioner ])
```

A specific verion of `getbasemeasure` defined particularly for distribution types from `Distributions.jl` package. Does not require an instance of the `ExponentialFamilyDistribution` and can be called directly with a specific distribution type instead. For conditional exponential family distributions requires an extra `conditioner` argument.
