```julia
function σ(x::UniData; 
    corrected::Bool=false, 
    centered::Bool=false, 
    mean::Realo=nothing) 
```

Population standard deviation of the elements in `x` or its unbiased sample estimator.

Call [`σ²`](@ref) with the same arguments and return its square root.
