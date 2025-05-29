```julia
function tsMap(	metric :: Metric, 𝐏 :: ℍVector;
    w           :: Vector = Float64[],
    ✓w         :: Bool = true,
    ⏩          :: Bool = true,
    meanISR     :: Union{ℍ, Nothing, UniformScaling}  = nothing,
    meanInit    :: Union{ℍ, Nothing}  = nothing,
    tol         :: Real = 0.,
    transpose   :: Bool = true,
    vecRange    :: UnitRange = 1:size(𝐏[1], 1))
```

The [tangent space mapping](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.logMap) of positive definite matrices $P_i$, *i=1...k* with mean *G*, once those points have been parallel transported to the identity matrix, is given by:

$S_i=\textrm{log}(G^{-1/2} P_i G^{-1/2})$.

Given a vector of *k* matrices `𝐏` flagged by julia as `Hermitian`, return a matrix *X* with such tangent vectors of the matrices in `𝐏` vectorized as per the [vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP) operation.

The mean *G* of the matrices in `𝐏` is found according to the specified `metric`, of type [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1). A natural choice is the [Fisher metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/introToRiemannianGeometry/#Fisher-1). If the metric is Fisher, logdet0 or Wasserstein the mean is found with an iterative algorithm with tolerance given by optional keyword argument `tol`. By default `tol` is set by the function [mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Statistics.mean). For those iterative algorithms a particular initialization can be provided as an Hermitian matrix by optional keyword argument `meanInit`.

A set of *k* optional non-negative weights `w` can be provided for computing a weighted mean *G*, for any metrics. If `w` is non-empty and optional keyword argument `✓w` is true (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized. This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

If an Hermitian matrix is provided as optional keyword argument `meanISR`, then the mean *G* is not computed, intead this matrix is used directly in the formula as the inverse square root (ISR) $G^{-1/2}$. If `meanISR` is provided, arguments `tol` and `meanInit` have no effect whatsoever.

If `meanISR=I` is used, then the tangent space mapping is obtained  at the identity matrix as

$S_i=\textrm{log}(P_i)$.

This corresponds to the tangent space mapping adopting the log-Euclidean metric. It is also useful when the data has been already recentered, for example by means of a [`Recenter`](@ref) pre-conditioner. If `meanISR=I` is used, arguments  `w`, `✓w`, `meanInit`, and `tol` are ignored.

If `meanISR` is not provided, return the 2-tuple $(X, G^{-1/2})$, otherwise return only matrix *X*.

If an `UnitRange` is provided with the optional keyword argument `vecRange`, the vectorization concerns only the columns (or rows) of the matrices `𝐏` specified by the range.

If optional keyword argument `transpose` is true (default), *X* holds the *k* vectorized tangent vectors in its rows, otherwise they are arranged in its columns. The dimension of the rows in the former case and of the columns is the latter case is *n(n+1)÷2* (integer division), where *n* is the size of the matrices in `𝐏`, unless a `vecRange` spanning a subset of the columns or rows of the matrices in `𝐏` has been provided, in which case the dimension will be smaller. (see [vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP) ).

if optional keyword argument `⏩` if true (default), the computation of the mean and the projection on the tangent space are multi-threaded. Multi-threading is automatically disabled if the number of threads Julia is instructed to use is *<2* or *<2k*.

**Examples**:

```julia
using PosDefManifoldML

# generate four random symmetric positive definite 3x3 matrices
Pset = randP(3, 4)

# project and vectorize in the tangent space
X, G⁻½ = tsMap(Fisher, Pset)

# X is a 4x6 matrix, where 6 is the size of the
# vectorized tangent vectors (n=3, n*(n+1)/2=6)

# If repeated calls have to be done, faster computations are obtained
# providing the inverse square root of the matrices in Pset, e.g.,
X1 = tsMap(Fisher, ℍVector(Pset[1:2]); meanISR = G⁻½)
X2 = tsMap(Fisher, ℍVector(Pset[3:4]); meanISR = G⁻½)
```

**See**: [the ℍVector type](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1).
