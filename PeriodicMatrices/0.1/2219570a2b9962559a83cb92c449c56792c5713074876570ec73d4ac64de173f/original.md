```
 tvmeval(At::PeriodicTimeSeriesMatrix, t; method = "linear") -> A::Vector{Matrix}
```

Evaluate the time response of a periodic time series matrix.

For the periodic time series matrix `At` and the vector of time values `t`,  an interpolation/extrapolation based approximation   `A[i]` is evaluated for each time value `t[i]`. The keyword parameter `method` specifies the interpolation/extrapolation method to be used for periodic data.  The following interpolation methods from the [`Interpolations.jl`](https://github.com/JuliaMath/Interpolations.jl)  package can be selected: 

`method = "constant"` - use periodic B-splines of degree 0; 

`method = "linear"` - use periodic B-splines of degree 1 (periodic linear interpolation) (default);

`method = "quadratic"` - use periodic B-splines of degree 2 (periodic quadratic interpolation); 

`method = "cubic"` - use periodic B-splines of degree 3 (periodic cubic interpolation).
