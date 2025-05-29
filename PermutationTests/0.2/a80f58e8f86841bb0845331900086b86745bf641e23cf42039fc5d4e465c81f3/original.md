```julia
function σ²(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing) 
```

Population variance of the $N$ elements in x (default), or its unbiased sample estimator if `corrected` is true.

If `centered` is true return the sum of the squared elements in `x` divided by $N$, or $N-1$ if  `corrected` is true,

otherwise,

call julia standard function `var` with arguments `corrected` and `mean`.
