```
fit(MULTISPATI, X, W, Q=I, D=I / size(X, 2); ...)
```

Perform MULTISPATI over the data given a matrix `X`. Each column of `X` is an **observation**. `W` is a connectivity matrix where $w_{ij}$ is the connection from j -> i. `Q` is a symmetric matrix of size `n` (or LinearAlgebra.UniformScaling(@ref))  and `D` a symmetric matrix of size `d` (or LinearAlgebra.UniformScaling(@ref)) 

**Keyword arguments**

  * `maxoutdim`: The output dimension, i.e. dimension of the transformed space (*min(d, nc-1)*)
  * `solver`: The choice of solver:

      * `:eig`: uses `LinearAlgebra.eigen` (*default*)
      * `:eigs`: uses `Arpack.eigs` (always used for sparse data)
  * `tol`: Convergence tolerance for `eigs` solver (*default* `0.0`)
  * `maxiter`: Maximum number of iterations for `eigs` solver (*default* `300`)

**References**

[S. Dray, et al. "Spatial ordination of vegetation data using a generalization of Wartenberg's  multivariate spatial correlation." *Journal of vegetation science* (2008)](https://doi.org/10.3170/2007-8-18312)

[de la Cruz and Holmes. "The duality diagram in data analysis: Examples of modern applications."  *The annals of applied statistics* (2011)](https://doi.org/10.1214/10-aoas408)
