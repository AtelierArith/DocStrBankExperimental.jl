```julia
    generalizedMean(𝐏::Union{ℍVector, 𝔻Vector}, p::Real;
    <
    w::Vector=[],
    ✓w=true,
    ⏩=true >)
```

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref) or real positive definite diagonal matrices of [𝔻Vector type](@ref) and optional non-negative real weights vector $w={w_1,...,w_k}$, return the *weighted generalized means* $G$ with real parameter $p$, that is,

$G=\big(\sum_{i=1}^{k}w_iP_i^p\big)^{1/p}$.

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted generalized mean*

$G=\big(\sum_{i=1}^{k}P_i^p\big)^{1/p}$.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized. This option is provided to allow calling this function repeatedly without normalizing the weights each time.

If *<optional key argmuent>* ⏩=true the computation of the generalized mean is multi-threaded.

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).


The following special cases for parameter $p$ are noteworthy:

  * For $p=\frac{1}{2}$ the generalized mean is the [modified Bhattacharyya mean](@ref).
  * For $p=1$ the generalized mean is the [Euclidean](@ref) mean.
  * For $p=-1$ the generalized mean is the [inverse Euclidean](@ref) mean.
  * For (the limit of) $p=0$ the generalized mean is the [log Euclidean](@ref) mean, which is the [Fisher](@ref) mean when matrices in 𝐏 all pair-wise commute.

Notice that when matrices in 𝐏 all pair-wise commute, for instance if the matrices are diagonal, the generalized means coincide with the [power means](@ref) for any $p∈[-1, 1]$ and for $p=0.5$ it coincides also with the [Wasserstein](@ref) mean. For this reason the generalized means are used as default initialization of both the [`powerMean`](@ref) and [`wasMean`](@ref) algorithm.

**See**: [generalized means](@ref).

**See also**: [`powerMean`](@ref), [`wasMean`](@ref), [`mean`](@ref).

**Examples**

```julia
using LinearAlgebra, Statistics, PosDefManifold
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4) # or, using unicode: 𝐏=randP(3, 4)

# weights vector, does not need to be normalized
weights=[1, 2, 3, 1]

# unweighted mean
G = generalizedMean(Pset, 0.25) # or: G = generalizedMean(𝐏, 0.25)

# weighted mean
G = generalizedMean(Pset, 0.5; w=weights)

# with weights previously normalized we can set ✓w=false
weights=weights./sum(weights)
G = generalizedMean(Pset, 0.5; w=weights, ✓w=false)

# run multi-threaded when the number of matrices is high
using BenchmarkTools
Pset=randP(20, 160)
@benchmark(generalizedMean(Pset; ⏩=false)) # single-threaded
@benchmark(generalizedMean(Pset)) # multi-threaded
```
