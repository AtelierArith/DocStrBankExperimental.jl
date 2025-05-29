```
freqresp!(R::Array{T, 3}, sys::LTISystem, w_vec::AbstractVector{<:Real})
```

In-place version of [`freqresp`](@ref) that takes a pre-allocated array `R` of size (ny, nu, nw)`
