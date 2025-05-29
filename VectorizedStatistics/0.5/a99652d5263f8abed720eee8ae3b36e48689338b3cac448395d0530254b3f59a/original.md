```julia
vcor(x::AbstractVector, y::AbstractVector, multithreaded=false)
```

Compute the (Pearson's product-moment) correlation between the vectors `x` and `y`. As `Statistics.cor`, but vectorized and (optionally) multithreaded.

Equivalent to `cov(x,y) / (std(x) * std(y))`.
