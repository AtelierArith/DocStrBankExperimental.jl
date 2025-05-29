```julia
    (1) distanceSqr(metric::Metric, P::ℍ{T}) where T<:RealOrComplex
    (2) distanceSqr(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
    (3) distanceSqr(metric::Metric, D::𝔻{S}) where S<:Real
    (4) distanceSqr(metric::Metric, D::𝔻{S}, E::𝔻{S}) where S<:Real
```

**alias**: `distance²`

(1) Return $δ^2(P, I)$, the *square of the distance* (or *divergence*) of positive definite matrix $P$ from the the identity matrix. See [distance from the origin](@ref).

(2) Return $δ^2(P, Q)$, the *square of the distance* (or *divergence*) between two positive definite matrices $P$ and $Q$. See [distance](@ref).

In both cases the distance function $δ$ is induced by the argument `metric` of type [Metric::Enumerated type](@ref).

$P$ in (1) and $P$, $Q$ in (2) must be flagged by julia as `Hermitian`. See [typecasting matrices](@ref).

(3) and (4) are specialized methods of (1) and (2), respectively, for real positive definite `Diagonal` matrices. See [ℍVector type](@ref) and [𝔻Vector type](@ref).

**Maths**

For point $P$ the *squared distances from the identity* for the supported metrics are:

|    Metric    | Squared Distance from the identity                                |
|:------------:|:----------------------------------------------------------------- |
|  Euclidean   | $∥P-I∥^2$                                                         |
| invEuclidean | $∥P^{-1}-I∥^2$                                                    |
| ChoEuclidean | $∥L_P-I∥^2$                                                       |
| logEuclidean | $∥\textrm{log}P∥^2$                                               |
| logCholesky  | $∥S_P∥^2+∥\textrm{log}D_P∥^2$                                     |
|    Fisher    | $∥\textrm{log}P∥^2$                                               |
|   logdet0    | $\textrm{logdet}\frac{1}{2}(P+I) - \frac{1}{2}\textrm{logdet}(P)$ |
|   Jeffrey    | $\frac{1}{2}\textrm{tr}(P+P^{-1})-n$                              |
|  VonNeumann  | $\frac{1}{2}\textrm{tr}(P\textrm{log}P-\textrm{log}P)$            |
| Wasserstein  | $\textrm{tr}(P+I) -2\textrm{tr}(P^{1/2})$                         |

For points $P$ and $Q$ their *squared distances* for the supported metrics are:

|    Metric    | Squared Distance                                                                      |
|:------------:|:------------------------------------------------------------------------------------- |
|  Euclidean   | $∥P-Q∥^2$                                                                             |
| invEuclidean | $∥P^{-1}-Q^{-1}∥^2$                                                                   |
| ChoEuclidean | $∥ L_P - L_Q ∥^2$                                                                     |
| logEuclidean | $∥\textrm{log}P-\textrm{log}Q∥^2$                                                     |
| logCholesky  | $∥S_P-S_Q∥^2+∥\textrm{log}D_P-\textrm{log}D_Q∥^2$                                     |
|    Fisher    | $∥\textrm{log}(P^{-1/2}QP^{-1/2})∥^2$                                                 |
|   logdet0    | $\textrm{logdet}\frac{1}{2}(P+Q) - \frac{1}{2}\textrm{logdet}(PQ)$                    |
|   Jeffrey    | $\frac{1}{2}\textrm{tr}(Q^{-1}P+P^{-1}Q)-n$                                           |
|  VonNeumann  | $\frac{1}{2}\textrm{tr}(P\textrm{log}P-P\textrm{log}Q+Q\textrm{log}Q-Q\textrm{log}P)$ |
| Wasserstein  | $\textrm{tr}(P+Q) -2\textrm{tr}(P^{1/2}QP^{1/2})^{1/2}$                               |

**legend:** $L_X$, $S_X$ and $D_X$ are the Cholesky lower triangle of $X$, its strictly lower triangular part and diagonal part, respectively (hence, $S_X+D_X=L_X$,  $L_XL_X^*=X$).

**See also**: [`distanceSqrMat`](@ref).

**Examples (1)**

```julia
using PosDefManifold
P=randP(10)
d=distanceSqr(Wasserstein, P)
e=distanceSqr(Fisher, P)
metric=Metric(Int(logdet0)) # or metric=logdet0
s=string(metric) # check what is the current metric
f=distance²(metric, P) #using the alias distance²
```

**Examples (2)**

```julia
using PosDefManifold
P=randP(10)
Q=randP(10)
d=distanceSqr(logEuclidean, P, Q)
e=distance²(Jeffrey, P, Q)
```
