```
lincom(r::AbstractDIDResult, linmap::AbstractMatrix{<:Real}, subset=nothing)
```

Linearly transform the coefficient estimates from DID result `r` through a matrix `linmap`. The number of columns of `linmap` must match the total number of coefficients from `r`. If `linmap` is not square (with fewer rows than columns), `subset` must be specified with indices representing coefficients that remain after the transformation. See also [`rescale`](@ref).
