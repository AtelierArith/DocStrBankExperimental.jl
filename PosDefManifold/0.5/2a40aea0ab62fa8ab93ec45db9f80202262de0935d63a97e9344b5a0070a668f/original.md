```julia
    (1) spectralEmbedding(metric::Metric, 𝐏::ℍVector, q::Int, epsilon::Real=0;
    <
    tol::Real=0.,
    maxiter::Int=300,
    densityInvariant=false,
    verbose=false,
    ⏩=true >)

    (2) spectralEmbedding(type::Type{T}, metric::Metric, 𝐏::ℍVector, q::Int, epsilon::Real=0;
    < same optional keyword arguments as in (1) >) where T<:Real
```

**alias**: `spEmb`

Given a 1d array $𝐏$ of $k$ positive definite matrices ${P_1,...,P_k}$ (real or complex), compute its *eigen maps* in $q$ dimensions.

This function runs one after the other the functions:

  * [`distanceSqrMat`](@ref) (compute the squared inter-distance matrix),
  * [`laplacian`](@ref) (compute the normalized Laplacian),
  * [`laplacianEigenMaps`](@ref) (get the eigen maps).

By default all computations above are done with `Float32` precision. Another real type can be requested using method (2), where the `type` argument is defined.

Return the 4-tuple `(Λ, U, iterations, convergence)`, where:

  * $Λ$ is a $q⋅q$ diagonal matrix holding on diagonal the eigenvalues corresponding to the $q$ dimensions of the Laplacian eigen maps,
  * $U$ holds in columns the $q$ eigenvectors holding the $q$ coordinates of the points in the embedding space,
  * $iterations$ is the number of iterations executed by the power method,
  * $convergence$ is the convergence attained by the power method.

**Arguments**:

  * `metric` is the metric of type [Metric::Enumerated type](@ref) used for computing the inter-distances,
  * $𝐏$ is a 1d array of $k$ positive matrices of [ℍVector type](@ref),
  * $q$ is the dimension of the Laplacian eigen maps,
  * $epsilon$ is the bandwidth of the Laplacian (see [`laplacian`](@ref));
  * The following *<optional keyword argument>* applyies for computing the inter-distances:
  * if `⏩=true` (default) the computation of inter-distances is multi-threaded.
  * The following *<optional keyword argument>* applyies to the computation of the Laplacian by the [`laplacian`](@ref) function:
  * if `densityInvariant=true` the density-invariant Laplacian is computed (see [`laplacian`](@ref)).
  * The following are *<optional keyword arguments>* for the power method iterative algorithm invoked by [`laplacianEigenMaps`](@ref):

      * `tol` is the tolerance for convergence of the power method (see below),
      * `maxiter` is the maximum number of iterations allowed for the power method,
      * if `verbose=true` the convergence at all iterations will be printed;

!!! note "Nota Bene"
    $tol$ defaults to the square root of `Base.eps` of the `Float32` type (1) or of the `type` passed as argumant (2). This corresponds to requiring equality for the convergence criterion over two successive power iterations of about half of the significant digits.

    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).


**See also**: [`distanceSqrMat`](@ref), [`laplacian`](@ref), [`laplacianEigenMaps`](@ref).

**Examples**

```julia
using PosDefManifold
# Generate a set of k random 10x10 SPD matrices
k=10
Pset=randP(10, k)
evalues, maps, iter, conv=spectralEmbedding(Fisher, Pset, 2)

# show convergence information
evalues, maps, iter, conv=spectralEmbedding(Fisher, Pset, 2; verbose=true)

# use Float64 precision.
evalues, maps, iter, conv=spectralEmbedding(Float64, Fisher, Pset, 2)

using Plots
# check eigevalues and eigenvectors
plot(diag(evalues))
plot(maps[:, 1])
plot!(maps[:, 2])
plot!(maps[:, 3])

# plot the data in the embedded space
plot(maps[:, 1], maps[:, 2], seriestype=:scatter, title="Spectral Embedding", label="Pset")

# try a different value of epsilon
evalues, maps, iter, conv=spEmb(Fisher, Pset, k-1, 0.01; maxiter=1000)
plot(maps[:, 1], maps[:, 2], seriestype=:scatter, title="Spectral Embedding", label="Pset")
# see the example in `Laplacian` function for more on this
```
