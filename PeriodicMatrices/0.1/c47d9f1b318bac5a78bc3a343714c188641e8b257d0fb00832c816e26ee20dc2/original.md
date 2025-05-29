```
 ts2fm(A::Vector{<:AbstractMatrix}, period; method = "linear") -> At::Function
```

Compute the function matrix corresponding to an interpolated matrix time series.  For the given matrix time series `A`, a function matrix `A(t)` is defined as the  mapping `A(t) = t -> Aint(t)`, where `Aint(t)` is an array of interpolation objects,   as provided in the [`Interpolations.jl`](https://github.com/JuliaMath/Interpolations.jl)  package.  The keyword parameter `method` specifies the interpolation method to be used as follows:

`method = "constant"` - use periodic B-splines of degree 0 (constant interpolation);

`method = "linear"` - use periodic B-splines of degree 1 (linear interpolation) (default);

`method = "quadratic"` - use periodic B-splines of degree 2 (quadratic interpolation); 

`method = "cubic"` - use periodic B-splines of degree 3 (cubic interpolation). 
