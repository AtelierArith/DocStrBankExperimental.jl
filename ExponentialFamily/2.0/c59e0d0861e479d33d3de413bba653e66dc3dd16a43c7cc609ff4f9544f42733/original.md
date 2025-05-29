```
getlogbasemeasure(::Type{<:Distribution}, [ conditioner ])
```

A generic verion of `getbasemeasure` defined particularly for distribution types from `Distributions.jl` package. For conditional exponential family distributions requires an extra `conditioner` argument. Just computes log of basemeasure.
