```julia
    geometricpMean(𝐏::ℍVector, p::Real=0.5;
    <
    w::Vector=[],
    ✓w=true,
    init=nothing,
    tol::Real=0.,
    maxiter::Int=500,
    adaptStepSize=true,
    verbose=false,
    ⏩=true >)
```

**alias**: `gpmean`

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref), a real parameter $0<p<=1$ and optional non-negative real weights vector $w={w_1,...,w_k}$, return the 3-tuple $(G, iter, conv)$, where $G$ is the *p-mean*, i.e., the mean according to the [Fisher](@ref) metric minimizing the *p-dispersion* (see below) and $iter$, $conv$ are the number of iterations and convergence attained by the algorithm.

This function implements the p-dispersion gradient descent algorithm with step-size $ς$ (to be published), yielding iterations

$G ←G^{1/2}\textrm{exp}\big(ς\sum_{i=1}^{k}pδ^2(G, P_i)^{p-1}w_i\textrm{log}(G^{-1/2} P_i G^{-1/2})\big)G^{1/2}.$

  * if $p=1$ this yields the geometric mean (implemented specifically in [`geometricMean`](@ref)).
  * if $p=0.5$ this yields the geometric median (default).

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted geometric-p mean*.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized.  This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

The following are more *<optional keyword arguments*>:

  * `init` is a matrix to be used as initialization for the mean. If no matrix is provided, the [Euclidean](@ref) mean will be used,
  * `tol` is the tolerance for the convergence (see below).
  * `maxiter` is the maximum number of iterations allowed.
  * if `adaptStepSize`=true (default) the step size $ς$ for the gradient descent is adapted at each iteration (see below).
  * if `verbose`=true, the step-size and convergence attained at each iteration is printed. Also, a *warning* is printed if convergence is not attained.
  * if ⏩=true the iterations are multi-threaded (see below).

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).

    If the algorithm diverges and `verbose` is true a **warning** is printed indicating the iteration when this happened. This algorithm may temporary diverge, still reach convergence. Overall, while all other iterative algorithms implemented in **PosDefMaifold** are very stable, this is not.

    The smaller the parameter $p$ is, the slower and less likely the convergence is. If the algorithm does not converge, try increasing $p$, initializing the algorithm with the output of [`geometricMean`](@ref) and/or eliminating the otliers from the input set $𝐏$.

    If `adaptStepSize` is true (default) the step-size $ς$ is adapted at each iteration, otherwise a fixed step size $ς=1$ is used. Adapting the step size in general hastens convergence and improves the convergence behavior.

    $tol$ defaults to the square root of `Base.eps` of the nearest real type of data input $𝐏$. This corresponds to requiring the norm of the satisfying matrix equation divided by the number of elements to vanish for about half the significant digits.


**See**: [Fisher](@ref) metric.

**See also**: [`geometricMean`](@ref), [`powerMean`](@ref), [`wasMean`](@ref), [`logdet0Mean`](@ref), [`mean`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold, Plots

# This examples show that this algorithm is more robust to outliers
# as compared to the standard geometric mean algorithm

# Generate a set of 100 random 10x10 SPD matrices
Pset=randP(10, 100)

# Get the usual geometric mean for comparison
G, iter1, conv1 = geometricMean(Pset, verbose=true)

# change p to observe how the convergence behavior changes accordingly
# Get the median (default)
H, iter2, conv2 = geometricpMean(Pset, verbose=true)
# Get the p-mean for p=0.25
H, iter2, conv2 = geometricpMean(Pset, 0.25, verbose=true)

println(iter1, " ", iter2); println(conv1, " ", conv2)

# move the first matrix in Pset to possibly create an otlier
Pset[1]=geodesic(Fisher, G, Pset[1], 3)
G1, iter1, conv1 = geometricMean(Pset, verbose=true)
H1, iter2, conv2 = geometricpMean(Pset, 0.25, verbose=true)
println(iter1, " ", iter2); println(conv1, " ", conv2)

# collect the geometric and p-means, before and after the
# introduction of the outier in vector of Hermitian matrices `S`.
S=HermitianVector([G, G1, H, H1])

# check the interdistance matrix Δ² to verify that the geometric mean
# after the introduction of the outlier (``G1``) is farther away from
# the geometric mean as compared to how much ``H1`` is further away
# from ``H``, i.e., that element (4,3) is much smaller than element (2,1).
Δ²=distance²Mat(Float64, Fisher, S)

# how far are all these matrices from all the others?
fullΔ²=Hermitian(Δ², :L)
dist=[sum(fullΔ²[:, i]) for i=1:size(fullΔ², 1)]

# plot the matrices in `S` using spectral embedding.
using Plots
Λ, U, iter, conv = laplacianEM(laplacian(Δ²), 3;  verbose=true)
plot([U[1, 1]], [U[1, 2]], seriestype=:scatter, label="g-mean")
plot!([U[2, 1]], [U[2, 2]], seriestype=:scatter, label="g-mean outlier")
plot!([U[3, 1]], [U[3, 2]], seriestype=:scatter, label="p-mean")
plot!([U[4, 1]], [U[4, 2]], seriestype=:scatter, label="p-mean outlier")

# estimate how much you gain running the algorithm in multi-threaded mode
using BenchmarkTools
Pset=randP(20, 120)
@benchmark(geometricpMean(Pset; ⏩=true)) # single-threaded
@benchmark(geometricpMean(Pset)) # multi-threaded
```
