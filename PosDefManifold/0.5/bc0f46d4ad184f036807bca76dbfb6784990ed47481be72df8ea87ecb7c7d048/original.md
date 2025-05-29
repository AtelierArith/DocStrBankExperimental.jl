```julia
    wasMean(𝐏::Union{ℍVector, 𝔻Vector};
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    verbose=false,
    ⏩=true >)
```

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref) or real positive definite diagonal matrices of [𝔻Vector type](@ref) and optional non-negative real weights vector $w={w_1,...,w_k}$, return the 3-tuple $(G, iter, conv)$, where $G$ is the mean according to the [Wasserstein](@ref) metric and $iter$, $conv$ are the number of iterations and convergence attained by the algorithm. Mean $G$ is the unique positive definite matrix satisfying

$G=\sum_{i=1}^{k}w_i\big( G^{1/2}  P_i G^{1/2}\big)^{1/2}$.

For estimating it, this function implements the fixed-point iterative algorithm proposed by (Álvarez-Esteban et *al.*, 2016)[🎓](@ref):

$G ← G^{-1/2}\big(\sum_{i=1}^{k} w_i(G^{1/2}P_i G^{1/2})^{1/2}\big)^2 G^{-1/2}$.

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted Wassertein mean*.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and they should be already normalized.  This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

The following are more *<optional keyword arguments*>:

  * `init` is a matrix to be used as initialization for the mean. If no matrix is provided, the instance of [generalized means](@ref) with $p=0.5$ will be used,
  * `tol` is the tolerance for the convergence (see below).
  * `maxiter` is the maximum number of iterations allowed.
  * if `verbose`=true, the convergence attained at each iteration is printed and a *warning* is printed if convergence is not attained.
  * if ⏩=true the iterations are multi-threaded (see below).

If the input is a 1d array of $k$ real positive definite diagonal matrices the solution is available in closed-form as the modified Bhattacharyya mean, hence the *<optional keyword arguments*> `init`, `tol` and `verbose` have no effect and return the 3-tuple $(G, 1, 0)$. See [modified Bhattacharyya mean](@ref).

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).

    In normal circumstances this algorithm converges monothonically. If the algorithm diverges and `verbose` is true a **warning** is printed indicating the iteration when this happened.

    $tol$ defaults to the square root of `Base.eps` of the nearest real type of data input $𝐏$. This corresponds to requiring the norm of the satisfying matrix equation divided by the number of elements to vanish for about half the significant digits.


**See**: [Wasserstein](@ref) metric.

**See also**: [`powerMean`](@ref), [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4) # or, using unicode: 𝐏=randP(3, 4)

# unweighted mean
G, iter, conv = wasMean(Pset) # or: G, iter, conv = wasMean(𝐏)

# weights vector, does not need to be normalized
weights=[1, 2, 3, 1]

# weighted mean
G, iter, conv = wasMean(Pset; w=weights)

# print the convergence at all iterations
G, iter, conv = wasMean(Pset; w=weights, verbose=true)

# suppose 𝐏 has changed a bit; initialize with G to hasten convergence
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = wasMean(Pset; w=weights, verbose=true, init=G)

# estimate how much you gain running the algorithm in multi-threaded mode
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(wasMean(Pset; ⏩=false)) # single-threaded
@benchmark(wasMean(Pset)) # multi-threaded
```
