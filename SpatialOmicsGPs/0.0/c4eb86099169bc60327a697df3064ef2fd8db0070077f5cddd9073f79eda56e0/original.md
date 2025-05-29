```
spatialde_varpars_all(y,x::Union{RowVecs, ColVecs},n::Int; covariates = [], mean = true, lambda_tol = 1e-3)
```

Compute the spatial variance parameters for all variables (columns) in `y` observed at locations `x` using FaST-LMM with a squared exponential kernel and a grid of length scales.  The input `x` should be of type `RowVecs` or `ColVecs` from the `KernelFunctions` package.
