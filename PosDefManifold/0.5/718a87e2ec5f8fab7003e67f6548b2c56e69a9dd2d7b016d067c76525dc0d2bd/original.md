```julia
    logdet0Mean(𝐏::Union{ℍVector, 𝔻Vector};
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    verbose=false,
    ⏩=true >)
```

**alias**: `ld0Mean`

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref) or real positive definite diagonal matrices of [𝔻Vector type](@ref) and optional non-negative real weights vector $w={w_1,...,w_k}$, return the 3-tuple $(G, iter, conv)$, where $G$ is the mean according to the [logdet zero](@ref) metric and $iter$, $conv$ are the number of iterations and convergence attained by the algorithm. Mean $G$ is the unique positive definite matrix satisfying

$\sum_{i=1}^{k}w_i\big(\frac{1}{2}P_i+\frac{1}{2}G\big)^{-1}-G^{-1}=0$.

For estimating it, this function implements the fixed-point iteration algorithm suggested by (Moakher, 2012, p315)[🎓](@ref), yielding iterations

$G ← \frac{1}{2}\big(\sum_{i=1}^{k}w_i(P_i+G)^{-1}\big)^{-1}$.

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted logdet zero mean*.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized.  This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

The following are more *<optional keyword arguments*>:

  * `init` is a matrix to be used as initialization for the mean. If no matrix is provided, the [Euclidean](@ref) mean will be used,
  * `tol` is the tolerance for the convergence (see below).
  * `maxiter` is the maximum number of iterations allowed.
  * if `verbose`=true, the convergence attained at each iteration is printed and a *warning* is printed if convergence is not attained.
  * if ⏩=true the iterations are multi-threaded (see below).

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).

    In normal circumstances this algorithm converges monothonically. If the algorithm diverges and `verbose` is true a **warning** is printed indicating the iteration when this happened.

    $tol$ defaults to 100 times the square root of `Base.eps` of the nearest real type of data input $𝐏$. This corresponds to requiring the square root of the relative convergence criterion over two successive iterations to vanish for about half the significant digits minus 2.


**See**: [logdet zero](@ref) metric, [modified Bhattacharyya mean](@ref).

**See also**: [`powerMean`](@ref), [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4) # or, using unicode: 𝐏=randP(3, 4)

# unweighted mean
G, iter, conv = logdet0Mean(Pset) # or G, iter, conv = logdet0Mean(𝐏)

# weights vector, does not need to be normalized
weights=[1, 2, 3, 1]

# weighted mean
G, iter, conv = logdet0Mean(Pset, w=weights)

# print the convergence at all iterations
G, iter, conv = logdet0Mean(Pset; w=weights, verbose=true)

# suppose Pset has changed a bit; initialize with G to hasten convergence
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = logdet0Mean(Pset; w=weights, ✓w=false, verbose=true, init=G)

# estimate how much you gain running the algorithm in multi-threaded mode
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(logdet0Mean(Pset; ⏩=false)) # single-threaded
@benchmark(logdet0Mean(Pset)) # multi-threaded
```
