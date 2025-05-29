```julia
    (1) mean(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex

    (2) mean(metric::Metric, D::𝔻{T}, E::𝔻{T}) where T<:Real

    (3) mean(metric::Metric, 𝐏::ℍVector;
        <
        w::Vector=[],
        ✓w=true,
        init::Union{ℍ, Nothing}=nothing,
        tol::Real=0.,
        verbose=false,
        ⏩=true >)

    (4) mean(metric::Metric, 𝐃::𝔻Vector;
    < same optional keyword arguments as in (3) >)
```

(1) Mean of two positive definite matrices, passed in arbitrary order as arguments $P$ and $Q$, using the specified `metric` of type [Metric::Enumerated type](@ref). The order is arbitrary as all metrics implemented in **PosDefManifold** are symmetric. This is the midpoint of the geodesic. For the weighted mean of two positive definite matrices use instead the [`geodesic`](@ref) function. $P$ and $Q$ must be flagged as `Hermitian`. See [typecasting matrices](@ref).

(2) Like in (1), but for two real diagonal positive definite matrices $D$ and $E$.

(3) [Fréchet mean](@ref) of an 1d array $𝐏$ of $k$ positive definite matrices $𝐏={P_1,...,P_k}$ of [ℍVector type](@ref), with optional non-negative real weights $w={w_1,...,w_k}$ and using the specified `metric`as in (1).

(4) [Fréchet mean](@ref) of an 1d array $𝐃$ of $k$ positive definite matrices $𝐃={D_1,...,D_k}$ of [𝔻Vector type](@ref), with optional non-negative real weights $w={w_1,...,w_k}$ and using the specified `metric`as in (1).

If you don't pass a weight vector with *<optional keyword argument>* $w$, return the *unweighted mean*.

If *<optional keyword argument>* `✓w=true` (default), the weights are normalized so as to sum up to 1, otherwise they are used as they are passed and should be already normalized.  This option is provided to allow calling this function repeatedly without normalizing the same weights vector each time.

Adopting the `Fisher`, `logdet0` and `Wasserstein` metric in (3) and the `logdet0` metric in (4), the mean is computed by means of an iterative algorithm. A particular initialization for these algorithms can be provided passing an Hermitian matrix as *<optional keyword argument>* `init`. The convergence for these algorithm is required with a tolerance given by *<optional keyword argument>* `tol`. if `verbose=true` the covergence attained at each iteration is printed. Other information such as if the algorithm has diverged is also printed. For more options in computing these means call directly functions [`geometricMean`](@ref), [`logdet0Mean`](@ref) and [`wasMean`](@ref), which are called hereby. For the meaning of the `tol` default value see the documentation of these functions. See also the robust mean function [`geometricpMean`](@ref), which cannot be called from here. Notice that arguments `init` and `tol` have an effect only for the aferomentioned metrics in methods (3) and (4).

For (3) and (4), if `⏩=true` (default), the computation of the mean is multi-threaded for all metrics.

!!! note "Nota Bene"
    [Multi-threading](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) is automatically disabled if Julia is instructed to use only one thread. See [Threads](@ref).


## Math

The Fréchet mean of a set of $k$ matrices ${P_1, P_2,..., P_k}$ weighted by ${w_1, w_2,..., w_k}:\sum_{i=1}^{k}w_i=1$ for the supported metrics are, for those with closed form expression:

|    Metric    | weighted Fréchet mean                                                       |
|:------------:|:--------------------------------------------------------------------------- |
|  Euclidean   | $\sum_{i=1}^{k}w_i P_i$                                                     |
| invEuclidean | $\big(\sum_{i=1}^{k}w_i P_i^{-1}\big)^{-1}$                                 |
| ChoEuclidean | $TT^*$, where $T=bL_P + aL_Q$                                               |
| logEuclidean | $\textrm{exp}\big(\sum_{i=1}^{k}w_i\hspace{1pt} \textrm{log}P_i \big)$      |
| logCholesky  | $TT^*$, where $T=\sum_{i=1}^{k}(w_kS_k)+\sum_{i=1}^{k}(w_k\textrm{log}D_k)$ |
|   Jeffrey    | $A^{1/2}\big(A^{-1/2}HA^{-1/2}\big)^{1/2}A^{1/2}$                           |

and for those that are found by an iterative algorithm and that verify an equation:

|   Metric    | equation verified by the weighted Fréchet mean                       |
|:-----------:|:-------------------------------------------------------------------- |
|   Fisher    | $\sum_{i=1}^{k}w_i\textrm{log}\big(G^{-1/2} P_k G^{-1/2}\big)=0.$    |
|   logdet0   | $\sum_{i=1}^{k}w_i\big(\frac{1}{2}P_i+\frac{1}{2}G\big)^{-1}=G^{-1}$ |
| VonNeumann  | N.A.                                                                 |
| Wasserstein | $G=\sum_{i=1}^{k}w_i\big( G^{1/2}  P_i G^{1/2}\big)^{1/2}$           |

**legend:** $L_X$, $S_X$ and $D_X$ are the Cholesky lower triangle of $X$, its strictly lower triangular part and diagonal part, respectively (hence, $S_X+D_X=L_X$,  $L_XL_X^*=X$). $A$ and $H$ are the weighted arithmetic and weighted harmonic mean, respectively.

**See**: [geodesic](@ref), [mean](@ref), [Fréchet mean](@ref).

**Examples**

```julia
using LinearAlgebra, Statistics, PosDefManifold
# Generate 2 random 3x3 SPD matrices
P=randP(3)
Q=randP(3)
M=mean(logdet0, P, Q) # (1)
M=mean(Euclidean, P, Q) # (1)

# passing several matrices and associated weights listing them
# weights vector, does not need to be normalized
R=randP(3)
mean(Fisher, ℍVector([P, Q, R]); w=[1, 2, 3])

# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4)
weights=[1, 2, 3, 1]
# passing a vector of Hermitian matrices (ℍVector type)
M=mean(Euclidean, Pset; w=weights) # (2) weighted Euclidean mean
M=mean(Wasserstein, Pset)  # (2) unweighted Wassertein mean
# display convergence information when using an iterative algorithm
M=mean(Fisher, Pset; verbose=true)

# run multi-threaded when the number of matrices is high
using BenchmarkTools
Pset=randP(20, 160)
@benchmark(mean(logEuclidean, Pset; ⏩=false)) # single-threaded
@benchmark(mean(logEuclidean, Pset)) # multi-threaded
```
