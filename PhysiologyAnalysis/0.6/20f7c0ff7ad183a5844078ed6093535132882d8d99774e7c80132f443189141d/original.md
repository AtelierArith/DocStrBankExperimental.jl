```
function IRfit(intensity::AbstractArray{T}, response::AbstractArray{T};
    lb::AbstractArray{T} = [1.0, 1.0, 0.1], #Default rmin = 100, kmin = 0.1, nmin = 0.1 
    p0::AbstractArray{T} = [500.0, 1000.0, 2.0], #Default r = 500.0, k = 200.0, n = 2.0
    ub::AbstractArray{T} = [Inf, Inf, 10.0], #Default rmax = 2400, kmax = 800
) where {T<:Real}
```

This function takes X and Y values and fits them according to a HILL type fit
