```
kss(X::AbstractMatrix{<:Real}, d::AbstractVector{<:Integer};
    maxiters = 100,
    rng = default_rng(),
    Uinit = [randsubspace(rng, size(X, 1), di) for di in d])
```

Cluster the `N` data points in the `D×N` data matrix `X` into `K` clusters via the **K**-**s**ub**s**paces (KSS) algorithm with corresponding subspace dimensions `d[1],...,d[K]`. Output is a [`KSSResult`](@ref) containing the resulting cluster assignments `c[1],...,c[N]`, subspace basis matrices `U[1],...,U[K]`, and metadata about the algorithm run.

KSS seeks to cluster data points by their subspace by minimizing the following total cost

$$
\sum_{i=1}^N \| X[:, i] - U[c[i]] U[c[i]]' X[:, i] \|_2^2
$$

with respect to the cluster assignments `c[1],...,c[N]` and subspace basis matrices `U[1],...,U[K]`.

# Keyword arguments

  * `maxiters::Integer = 100`: maximum number of iterations
  * `rng::AbstractRNG = default_rng()`: random number generator   (used when reinitializing the subspace for an empty cluster)
  * `Uinit::AbstractVector{<:AbstractMatrix{<:AbstractFloat}}   = [randsubspace(rng, size(X, 1), di) for di in d]`:   vector of `K` initial subspace basis matrices to use   (each `Uinit[k]` should be `D×d[k]`)

See also [`KSSResult`](@ref).
