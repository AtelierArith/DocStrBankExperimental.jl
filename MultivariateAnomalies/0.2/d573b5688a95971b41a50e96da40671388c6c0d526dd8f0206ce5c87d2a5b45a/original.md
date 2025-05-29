```
mapMovingWindow(function2mw, x, args...; ObsPerYear::Int = 46, windowsize::Int = 9, edgecut::Int = 0, startidx::Int = 1, numoutvars::Int = 0)
mapMovingWindow(function2mw, x; ...)
```

apply a function (function2mw) in a moving window encompassing all years and running along the time, e.g. apply the function to all summers, then summers + 1 timestep ... results are written to the center of the respective windowsize. Input axes are time or time-variables. The number of output variables can be different from the number of input variables, specified in numoutvars. e.g. transforming the variables in normalised ranks between zero and one to get rid of heteroscedasticity would look like:     using MultivariateAnomalies     x = randn(10*46, 3)     mapMovingWindow(get*quantile*scores, x, numoutvars = size(x, 2))
