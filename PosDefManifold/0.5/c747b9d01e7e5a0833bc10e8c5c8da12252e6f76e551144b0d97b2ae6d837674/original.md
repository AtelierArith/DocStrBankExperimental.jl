```julia
    (1) distanceSqrMat(metric::Metric, 𝐏::ℍVector;
    <⏩=true>)

    (2) distanceSqrMat(type::Type{T}, metric::Metric, 𝐏::ℍVector;
    <⏩=true>) where T<:AbstractFloat
```

**alias**: `distance²Mat`

Given a 1d array $𝐏$ of $k$ positive definite matrices ${P_1,...,P_k}$ of [ℍVector type](@ref), create the $k⋅k$ real `LowerTriangular` matrix comprising elements $δ^2(P_i, P_j)\textrm{, for all }i>=j$.

This is the lower triangular matrix holding all *squared inter-distances* (zero on diagonal), using the specified `metric`, of type [Metric::Enumerated type](@ref), giving rise to distance function $δ$. See [`distanceSqr`](@ref).

Only the lower triangular part is computed in order to optimize memory use.

By default, the result matrix is of type `Float32`. The type can be changed to another real `type` using method (2).

<optional keyword arguments>:

  * if ⏩=true (default) the computation of inter-distances is multi-threaded.

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).


**See**: [distance](@ref).

**See also**: [`laplacian`](@ref), [`laplacianEigenMaps`](@ref), [`spectralEmbedding`](@ref).

**Examples**

```julia
using PosDefManifold
# Generate a set of 8 random 10x10 SPD matrices
Pset=randP(10, 8) # or, using unicode: 𝐏=randP(10, 8)
# Compute the squared inter-distance matrix according to the log Euclidean metric.
# This is much faster as compared to the Fisher metric and in general
# it is a good approximation.
Δ²=distanceSqrMat(logEuclidean, Pset)

# return a matrix of type Float64
Δ²64=distanceSqrMat(Float64, logEuclidean, Pset)

# Get the full matrix of inter-distances
fullΔ²=Hermitian(Δ², :L)
```
