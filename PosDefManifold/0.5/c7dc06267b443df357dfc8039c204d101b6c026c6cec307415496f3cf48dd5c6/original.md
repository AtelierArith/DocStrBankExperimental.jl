```julia
    geometricMean(𝐏::Union{ℍVector, 𝔻Vector};
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=200,
    adaptStepSize::Bool=true,
    verbose=false,
    ⏩=true >)
```

**alias**: `gMean`

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref) or diagonal matrices of [𝔻Vector type](@ref) and optional non-negative real weights vector $w={w_1,...,w_k}$, return the 3-tuple $(G, iter, conv)$, where $G$ is the mean according to the [Fisher](@ref) metric and $iter$, $conv$ are the number of iterations and convergence attained by the algorithm. Mean $G$ is the unique positive definite matrix satisfying

$\sum_{i=1}^{k}w_i\textrm{log}\big(G^{-1/2} P_i G^{-1/2}\big)=0.$

For estimating it, this function implements the well-known gradient descent algorithm, but with an exponential decaying step size $ς$, yielding iterations

$G ← G^{1/2}\textrm{exp}\big(ς\sum_{i=1}^{k}w_i\textrm{log}(G^{-1/2} P_i G^{-1/2})\big)G^{1/2}.$

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted geometric mean*.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized.  This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

The following are more *<optional keyword arguments*>:

  * `init` is a matrix to be used as initialization for the mean. If no matrix is provided, the [Euclidean](@ref) mean will be used,
  * `tol` is the tolerance for the convergence (see below).
  * `maxiter` is the maximum number of iterations allowed
  * if `verbose`=true, the convergence attained at each iteration and the step size $ς$ is printed. Also, a *warning* is printed if convergence is not attained.
  * if ⏩=true the iterations are multi-threaded (see below).
  * if `adaptStepSize`=false the step size `ς` is fixed to 1 at all iterations.

If the input is a 1d array of $k$ real positive definite diagonal matrices the solution is available in closed-form as the log Euclidean mean, hence the *<optional keyword arguments*> `init`, `tol` and `verbose` have no effect and return the 3-tuple $(G, 1, 0)$. See the [log Euclidean](@ref) metric.

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).

    In normal circumstances this algorithm converges monothonically. If the algorithm diverges and `verbose` is true a **warning** is printed indicating the iteration when this happened.

    The exponential decaying step size features a faster convergence rate as compared to the fixed step size $ς=1$ that is usually adopted. The decaying rate is inversely proportional to `maxiter`, thus, increase/decrease `maxiter` in order to set a slower/faster decaying rate. `maxiter` should not be set too low though.

    $tol$ defaults to the square root of `Base.eps` of the nearest real type of data input $𝐏$. This corresponds to requiring the norm of the satisfying matrix equation divided by the number of elements to vanish for about half the significant digits.


**See**: [Fisher](@ref) metric.

**See also**: [`geometricpMean`](@ref), [`powerMean`](@ref),  [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4) # or, using unicode: 𝐏=randP(3, 4)

# unweighted mean
G, iter, conv = geometricMean(Pset) # or G, iter, conv = geometricMean(𝐏)

# weights vector, does not need to be normalized
weights=[1, 2, 3, 1]

# weighted mean
G, iter, conv = geometricMean(Pset, w=weights)

# print the convergence at all iterations
G, iter, conv = geometricMean(Pset; verbose=true)

# now suppose Pset has changed a bit, initialize with G to hasten convergence
Pset[1]=ℍ(Pset[1]+(randP(3)/100))
G, iter, conv = geometricMean(Pset; w=weights, ✓w=true, verbose=true, init=G)

# run multi-threaded when the number of matrices is high
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(geometricMean(Pset; ⏩=false)) # single-threaded
@benchmark(geometricMean(Pset)) # multi-threaded

# show the mean and the input points using spectral embedding
using Plots
k=80
Pset=randP(20, k)
G, iter, conv = geometricMean(Pset)
push!(Pset, G)
Λ, U, iter, conv=spectralEmbedding(Fisher, Pset, 2; verbose=true)
plot(U[1:k, 1], U[1:k, 2], seriestype=:scatter, title="Spectral Embedding", label="Pset")
plot!(U[k+1:k+1, 1], U[k+1:k+1, 2], seriestype=:scatter, label="mean")
```
