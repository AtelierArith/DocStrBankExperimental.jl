```julia
nancor(X::AbstractMatrix; dims::Int=1)
```

Compute the (Pearson's product-moment) correlation matrix of the matrix `X`, along dimension `dims`. As `Statistics.cor`, but ignoring `NaN`s.
