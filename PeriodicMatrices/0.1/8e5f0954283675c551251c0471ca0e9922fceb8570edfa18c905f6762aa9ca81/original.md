```
 ts2pfm(At::PeriodicTimeSeriesMatrix; method = "linear") -> A::PeriodicFunctionMatrix
```

Compute the periodic function matrix corresponding to an interpolated periodic time series matrix.  For the given periodic time series matrix `At`, a periodic function matrix `A(t)` is defined as the  mapping `A(t) = t -> etpf(t)`, where `etpf(t)` is a periodic interpolation/extrapolation object,   as provided in the [`Interpolations.jl`](https://github.com/JuliaMath/Interpolations.jl)  package.  The keyword parameter `method` specifies the interpolation/extrapolation method to be used as follows:

`method = "constant"` - use periodic B-splines of degree 0 (periodic constant interpolation);

`method = "linear"` - use periodic B-splines of degree 1 (periodic linear interpolation) (default);

`method = "quadratic"` - use periodic B-splines of degree 2 (periodic quadratic interpolation); 

`method = "cubic"` - use periodic B-splines of degree 3 (periodic cubic interpolation). 
