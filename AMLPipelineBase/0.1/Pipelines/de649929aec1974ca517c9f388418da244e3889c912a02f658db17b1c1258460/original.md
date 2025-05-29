```
ComboPipeline(machs::Vector{T}) where {T<:Machine}
```

Feature union pipeline which iteratively calls  `fit_transform` of each element and concatenate their output into one dataframe.

Implements `fit!` and `transform!`.
