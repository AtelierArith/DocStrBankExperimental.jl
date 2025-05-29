```
pseudo_svd([rng], [T], dims...; 
    max_value=1.0, sparsity=0.1, sorted=true, reverse_sort=false,
    return_sparse=false)
```

Returns an initializer to build a sparse reservoir matrix with the given `sparsity` by using a pseudo-SVD approach as described in [^yang2018].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `max_value`: The maximum absolute value of elements in the matrix. Default is 1.0
  * `sparsity`: The desired sparsity level of the reservoir matrix. Default is 0.1
  * `sorted`: A boolean indicating whether to sort the singular values before creating the diagonal matrix. Default is `true`.
  * `reverse_sort`: A boolean indicating whether to reverse the sorted singular values. Default is `false`.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.
  * `return_diag`: flag for returning a `Diagonal` matrix. If both `return_diag` and `return_sparse` are set to `true` priority is given to `return_diag`. Default is `false`.

# Examples

```jldoctest
julia> res_matrix = pseudo_svd(5, 5)
5×5 Matrix{Float32}:
 0.306998  0.0       0.0       0.0       0.0
 0.0       0.325977  0.0       0.0       0.0
 0.0       0.0       0.549051  0.0       0.0
 0.0       0.0       0.0       0.726199  0.0
 0.0       0.0       0.0       0.0       1.0
```

[^yang2018]: Yang, Cuili, et al. "*Design of polynomial echo state networks for time series prediction.*" Neurocomputing 290 (2018): 148-160.
