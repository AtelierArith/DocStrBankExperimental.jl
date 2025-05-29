```julia
    (1) distanceMat(metric::Metric, 𝐏::ℍVector;
    <⏩=true>)

    (2) distanceMat(type::Type{T}, metric::Metric, 𝐏::ℍVector;
    <⏩=true>) where T<:AbstractFloat
```

Given a 1d array $𝐏$ of $k$ positive definite matrices ${P_1,...,P_k}$ of [ℍVector type](@ref), create the $k⋅k$ real `LowerTriangular` matrix comprising elements $δ(P_i, P_j)\textrm{, for all }i>=j$.

This is the lower triangular matrix holding all *inter-distances* (zero on diagonal), using the specified `metric`, of type [Metric::Enumerated type](@ref), giving rise to distance $δ$. See [`distance`](@ref).

Only the lower triangular part is computed in order to optimize memory use.

By default, the result matrix is of type `Float32`. The type can be changed to another real `type` using method (2).

The elements of this matrix are the square root of [`distanceSqrMat`](@ref).

<optional keyword arguments>:

  * if ⏩=true the computation of inter-distances is multi-threaded.

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).


**See**: [distance](@ref).

**Examples**

```julia
using PosDefManifold
# Generate a set of 4 random 10x10 SPD matrices
Pset=randP(10, 4) # or, using unicode: 𝐏=randP(10, 4)
Δ=distanceMat(Fisher, Pset)

# return a matrix of type Float64
Δ64=distanceMat(Float64, Fisher, Pset)

# Get the full matrix of inter-distances
fullΔ=Hermitian(Δ, :L)
```
