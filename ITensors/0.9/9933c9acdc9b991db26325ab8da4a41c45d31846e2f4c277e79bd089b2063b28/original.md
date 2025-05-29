```
hascommoninds(A, B; kwargs...)

hascommoninds(B; kwargs...) -> f::Function
```

Check if the ITensors or sets of indices `A` and `B` have common indices.

If only one ITensor or set of indices `B` is passed, return a function `f` such that `f(A) = hascommoninds(A, B; kwargs...)`
