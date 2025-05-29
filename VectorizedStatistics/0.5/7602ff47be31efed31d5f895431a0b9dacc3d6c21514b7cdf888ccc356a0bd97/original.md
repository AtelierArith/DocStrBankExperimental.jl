```julia
vcor(X::AbstractMatrix; dims::Int=1, multithreaded=false)
```

Compute the (Pearson's product-moment) correlation matrix of the matrix `X`, along dimension `dims`. As `Statistics.cor`, but vectorized and (optionally) multithreaded.
