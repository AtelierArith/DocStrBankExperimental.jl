```julia
    powerMean(𝐏::Union{ℍVector, 𝔻Vector}, p::Real;
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    verbose=false,
    ⏩=true >)
```

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref) or real positive definite diagonal matrices of [𝔻Vector type](@ref), an optional non-negative real weights vector $w={w_1,...,w_k}$ and a real parameter `p` $\in[-1, 1]$, return the 3-tuple $(G, iter, conv)$, where $G$ is Lim and Palfia (2012)'s [power means](@ref)  of order $p$ and $iter$, $conv$ are the number of iterations and convergence attained by the algorithm, respectively. Mean $G$ is the unique positive definite matrix satisfying

$G=\sum_{i=1}^{k}w_i(G\textrm{#}_pP_i)$,

where $G\textrm{#}_pP_i$ is the [Fisher](@ref) [geodesic](@ref) equation. In particular:

  * with $p=-1$ this is the *harmonic mean* (see the [inverse Euclidean](@ref) metric),
  * with $p=+1$ this is the *arithmetic mean* (see the [Euclidean](@ref) metric),
  * at the limit of $p$ evaluated at zero from both side this is the *geometric mean* (see [Fisher](@ref) metric).

For estimating power means for $p\in(-1, 1)$, this function implements the  fixed-point iterative algorithm of (Congedo et *al.*, 2017b)[🎓](@ref). For $p=0$ (geometric mean) this algorithm is run two times with a small positive and negative value of $p$ and the geometric mean of the two resulting means is returned, as suggested in (Congedo et *al.*, 2017b)[🎓](@ref). This way of estimating the geometric mean of a set of matrices is faster as compared to the usual gradient descent algorithm.

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted power mean*.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized.  This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

The following are more *<optional keyword arguments*>:

  * `init` is a matrix to be used as initialization for the mean. If no matrix is provided, the instance of [generalized means](@ref) with parameter $p$ will be used.
  * `tol` is the tolerance for the convergence (see below).
  * `maxiter` is the maximum number of iterations allowed.
  * if `verbose`=true, the convergence attained at each iteration is printed and a *warning* is printed if convergence is not attained.
  * if ⏩=true the iterations are multi-threaded.

If the input is a 1d array of $k$ real positive definite diagonal matrices the solution is available in closed-form as the generalized mean of order `p`, hence the *<optional keyword arguments*> `init`, `tol` and `verbose` have no effect and return the 3-tuple $(G, 1, 0)$. See [generalized means](@ref).

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).

    In normal circumstances this algorithm converges monothonically. If the algorithm diverges and `verbose` is true a **warning** is printed indicating the iteration when this happened.

    $tol$ defaults to the square root of `Base.eps` of the nearest real type of data input $𝐏$. This corresponds to requiring the norm of the difference of the matrix solution over two successive iterations divided by the number of elements in the matrix to vanish for about half the significant digits.


(2) Like in (1), but for a 1d array $𝐃={D_1,...,D_k}$ of $k$ real positive definite diagonal matrices of [𝔻Vector type](@ref). In this case the solution is available in closed-form, hence the *<optional keyword arguments*> `init`, `tol` and `verbose` have no effect and return the 3-tuple $(G, 1, 0)$. See [generalized means](@ref).

**See**: [power means](@ref), [generalized means](@ref), [modified Bhattacharyya mean](@ref).

**See also**: [`generalizedMean`](@ref), [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4) # or, using unicode: 𝐏=randP(3, 4)

# unweighted mean
G, iter, conv = powerMean(Pset, 0.5) # or G, iter, conv = powerMean(𝐏, 0.5)

# weights vector, does not need to be normalized
weights=[1, 2, 3, 1]

# weighted mean
G, iter, conv = powerMean(Pset, 0.5; w=weights)

# print the convergence at all iterations
G, iter, conv = powerMean(Pset, 0.5; w=weights, verbose=true)

# suppose 𝐏 has changed a bit; initialize with G to hasten convergence
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = powerMean(Pset, 0.5; w=weights, verbose=true, init=G)

# estimate how much you gain running the algorithm in multi-threaded mode
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(powerMean(Pset, 0.5; ⏩=false)) # single-threaded
@benchmark(powerMean(Pset, 0.5)) # multi-threaded
```
