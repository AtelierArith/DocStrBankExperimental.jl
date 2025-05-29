```
inrangecount(ss, query, r::Real; kwargs....) → n::Int
```

Count the amount of points `n` in the search structure `ss` that are witnin range `r` of the `query`. Typically provided that performs better than just getting the `length` of [`search`](@ref) with `WithinRange(r)`.
