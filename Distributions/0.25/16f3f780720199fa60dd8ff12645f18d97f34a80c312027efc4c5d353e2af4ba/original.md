```
LKJCholesky(d::Int, η::Real, uplo='L')
```

The `LKJCholesky` distribution of size $d$ with shape parameter $\eta$ is a distribution over `LinearAlgebra.Cholesky` factorisations of $d\times d$ real correlation matrices (positive-definite matrices with ones on the diagonal).

Variates or samples of the distribution are `LinearAlgebra.Cholesky` objects, as might be returned by `F = LinearAlgebra.cholesky(R)`, so that `Matrix(F) ≈ R` is a variate or sample of [`LKJ`](@ref). 

Sampling `LKJCholesky` is faster than sampling `LKJ`, and often having the correlation matrix in factorized form makes subsequent computations cheaper as well.

!!! note
    `LinearAlgebra.Cholesky` stores either the upper or lower Cholesky factor, related by `F.U == F.L'`. Both can be accessed with `F.U` and `F.L`, but if the factor not stored is requested, then a copy is made. The `uplo` parameter specifies whether the upper (`'U'`) or lower (`'L'`) Cholesky factor is stored when randomly generating samples. Set `uplo` to `'U'` if the upper factor is desired to avoid allocating a copy when calling `F.U`.


See [`LKJ`](@ref) for more details.

External links

  * Lewandowski D, Kurowicka D, Joe H. Generating random correlation matrices based on vines and extended onion method, Journal of Multivariate Analysis (2009), 100(9): 1989-2001 doi: [10.1016/j.jmva.2009.04.008](https://doi.org/10.1016/j.jmva.2009.04.008)
