```
concatenate!(X::LDLᵀ)
```

Concatenate the internal components such that `alpha`, `L` and `D` may be obtained via `alpha, L, D = X`. This function is roughly equivalent to `L = foldl(hcat, X.Ls)` and `D = foldl(dcat, Ds)`, where `dcat` is pseudo-code for "diagonal concatenation".

This is a somewhat cheap operation.

See also: [`compress!`](@ref)
