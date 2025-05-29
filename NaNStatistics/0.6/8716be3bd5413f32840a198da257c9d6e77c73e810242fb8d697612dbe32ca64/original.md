```julia
nancor(x::AbstractVector, y::AbstractVector)
```

Compute the (Pearson's product-moment) correlation between the vectors `x` and `y`. As `Statistics.cor`, but ignoring `NaN`s.

Equivalent to `nancov(x,y) / (nanstd(x) * nanstd(y))`.
