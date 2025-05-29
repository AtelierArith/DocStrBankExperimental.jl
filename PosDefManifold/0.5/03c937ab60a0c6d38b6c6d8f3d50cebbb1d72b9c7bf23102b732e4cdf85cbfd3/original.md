```julia
    (1) geodesic(metric::Metric, P::ℍ{T}, Q::ℍ{T}, a::Real) where T<:RealOrComplex
    (2) geodesic(metric::Metric, D::𝔻{S}, E::𝔻{S}, a::Real) where S<:Real
```

(1) Move along the [geodesic](@ref) from point $P$ to point $Q$ (two positive definite matrices) with *arclegth* $0<=a<=1$, using the specified metric, of type [Metric::Enumerated type](@ref).

For all metrics,

  * with $a=0$ we stay at $P$,
  * with $a=1$ we move up to $Q$,
  * with $a=1/2$ we move to the mid-point of $P$ and $Q$ (mean).

Using the Fisher metric, argument $a$ can be *any* real number, for instance:

  * with $0<a<1$ we move toward $Q$ (*attraction*),
  * with $a>1$ we move over and beyond $Q$ (*extrapolation*),
  * with $a<0$ we move back away from Q (*repulsion*).

$P$ and $Q$ must be flagged by julia as `Hermitian`. See [typecasting matrices](@ref).

The Fisher geodesic move is computed by the Cholesky-Schur algorithm given in Eq. 4.2 by Iannazzo(2016)[🎓](@ref). If $Q=I$, the Fisher geodesic move is simply $P^a$ (no need to call this funtion).

!!! note "Nota Bene"
    For the [logdet zero](@ref) and [Jeffrey](@ref) metric no closed form expression for the geodesic is available to the best of authors' knowledge, so in this case the geodesic is found as the weighted mean using the [`mean`](@ref) function. For the [Von Neumann](@ref) not even an expression for the mean is available, so in this case the geodesic is not provided and a *warning* is printed.


(2) Like in (1), but for two real positive definite diagonal matrices $D$ and $E$.

**Maths**

For points $P$, $Q$ and arclength $a$, letting $b=1-a$, the geodesic equations for the supported metrics are:

|    Metric    | geodesic equation                                                                                  |
|:------------:|:-------------------------------------------------------------------------------------------------- |
|  Euclidean   | $bP + aQ$                                                                                          |
| invEuclidean | $\big(bP^{-1} + aQ^{-1}\big)^{-1}$                                                                 |
| ChoEuclidean | $TT^*$, where $T=bL_P + aL_Q$                                                                      |
| logEuclidean | $\text{exp}\big(b\hspace{2pt}\text{log}(P) + a\hspace{2pt}\text{log}(Q)\big)$                      |
| logCholesky  | $TT^*$, where $T=S_P+a(S_Q-S_P)+D_P\hspace{2pt}\text{exp}\big(a(\text{log}D_Q-\text{log}D_P)\big)$ |
|    Fisher    | $P^{1/2} \big(P^{-1/2} Q P^{-1/2}\big)^a P^{1/2}$                                                  |
|   logdet0    | uses weighted mean algorithm [`logdet0Mean`](@ref)                                                 |
|   Jeffrey    | uses weighted mean [`mean`](@ref)                                                                  |
|  VonNeumann  | N.A.                                                                                               |
| Wasserstein  | $b^2P+a^2Q +ab\big[(PQ)^{1/2} +(QP)^{1/2}\big]$                                                    |

**legend:** $L_X$, $S_X$ and $D_X$    are the Cholesky lower triangle of $X$, its strictly lower triangular part    and diagonal part, respectively (hence, $S_X+D_X=L_X$,  $L_XL_X^*=X$).

**See also**: [`mean`](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(10)
Q=randP(10)
# Wasserstein mean
M=geodesic(Wasserstein, P, Q, 0.5)
# extrapolate suing the Fisher metric
E=geodesic(Fisher, P, Q, 2)
```
