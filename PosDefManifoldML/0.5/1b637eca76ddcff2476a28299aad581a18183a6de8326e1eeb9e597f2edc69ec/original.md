```julia
function distances(metric :: Metric,
                      means  :: ℍVector,
                      𝐏      :: ℍVector;
                imeans  :: Union{ℍVector, Nothing} = nothing,
                scale   :: Bool = false,
                ⏩      :: Bool = true)
```

Typically, you will not need this function as it is called by the [`predict`](@ref) function.

Given an [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) $𝐏$ holding *k* Hermitian matrices and an ℍVector `means` holding *z* matrix means, return the *square of the distance* of each matrix in $𝐏$ to the means in `means`.

The squared distance is computed according to the chosen `metric`, of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1). See [metrics](https://marco-congedo.github.io/PosDefManifold.jl/dev/introToRiemannianGeometry/#metrics-1) for details on the supported distance functions.

The computation of distances is optimized for the Fisher metric if an ℍVector holding the inverse of the means in `means` is passed as optional keyword argument `imeans`. For other metrics this argument is ignored.

If `scale` is true (default), the distances are divided by the size of the matrices in $𝐏$. This can be useful to compare distances computed on manifolds with different dimensions. It has no effect here, but is used as it is good practice.

If `⏩` is true, the distances are computed using multi-threading, unless the number of threads Julia is instructed to use is <2 or <3k.

The result is a *z*x*k* matrix of squared distances.
