```julia
function barycenter(metric :: Metric, 𝐏:: ℍVector;
              w        :: Vector = [],
              ✓w       :: Bool    = true,
              meanInit :: Union{ℍ, Nothing} = nothing,
              tol      :: Real   = 0.,
              ⏩      :: Bool    = true)
```

Typically, you will not need this function as it is called by the [`fit`](@ref) function.

Given a `metric` of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1), an [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) of Hermitian matrices $𝐏$ and an optional non-negative real weights vector `w`, return the (weighted) mean of the matrices in $𝐏$. This is used to fit MDM models.

This function calls the appropriate mean functions of package [PostDefManifold](https://marco-congedo.github.io/PosDefManifold.jl/dev/), depending on the chosen `metric`, and check that, if the mean is found by an iterative algorithm, then the iterative algorithm converges.

See method (3) of the [mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Statistics.mean) function for the meaning of the optional keyword arguments `w`, `✓w`, `meanInit`, `tol` and `⏩`, to which they are passed.

The returned mean is flagged by Julia as an Hermitian matrix (see [LinearAlgebra](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)).
