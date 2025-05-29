```
Z = get_design_matrix(x, nested=[]; maxlev=0, cov=false)
Z = get_design_matrix(x, y)
Z = get_design_matrix(X; maxlev=[], cov=[])
```

Returns a design matrix accoding to class variables or covariates in a vector `x` or matrix `X`. For a vector `x`, optional argument `dested` defines `x` as the nested covariate within a class. Option `maxval` specifies the number of levels in this effect. Omitting `maxval`, the function uses the maximum integer as the maximum level in `x` or `X`. Option `cov` specifies the input is covariate and passes it through the output. The matrix `X` doesn't support nested covariates.

If two vectors `x` and `y` are provided, the function returns the design matrix for the intercation between the two effects; the main effects are not included in the result. Also, in this case, the function does not accept any additional options.

```juliadoctest
julia> x = [1,2,1,1,2]
julia> X = get_design_matrix(x)
5×2 Array{Float64,2}:
 1.0  0.0
 0.0  1.0
 1.0  0.0
 1.0  0.0
 0.0  1.0
```
