```
spatialde_param_inference(y,x::Union{RowVecs, ColVecs},n::Int; covariates = [], mean = true, lambda_tol = 1e-3)
```

Perform parameter inference for the SpatialDE model for all variables (columns) in `y` observed at locations `x` with a squared exponential kernel and a grid of `n` length scales.  The input `x` should be of type `RowVecs` or `ColVecs` from the `KernelFunctions` package.  The function returns the optimal variance parameters and length scale indices for all variables, as well as the grid of length scales used. 
