```
lsdd(x::Array{Float64,1}, y::Array{Float64,1}; folds = 5, sigma_list = nothing, lambda_list = nothing)
Computes the least-squares density-difference (lsdd) for arrays `x` and `y`.
The lsdd value characterizes how different the probability densities the generated 'x' and 'y' are.
The closer the lsdd is to 0, the more similar the probability densities are.
Input :
    'x', 'y' : the arrays of data upon which to perform the lsdd computation.
    folds : the number of cross-validation tests. higher is more precise but more expensive.
    sigma_list, lambda_list : points defining the grid search during the optimization of gaussian kernels.
Returns :
    L2 : lsdd value.
```
