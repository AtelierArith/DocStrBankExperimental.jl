```julia
    (1) logMap(metric::Metric, P::ℍ{T}, G::ℍ{T})

    (2) logMap(metric::Metric, 𝐏::ℍVector, G::ℍ{T})
    for all the above: where T<:RealOrComplex
```

(1) *Logaritmic Map:* map a positive definite matrix $P$ from the SPD or Hermitian manifold into the tangent space at base-point $G$ using the [Fisher](@ref) metric.

$P$ and $G$ must be flagged as `Hermitian`. See [typecasting matrices](@ref).

The map is defined as

$Log_G(P)=S=G^{1/2}\textrm{log}\big(G^{-1/2}PG^{-1/2}\big)G^{1/2}$.

`metric` is a metric of type [Metric::Enumerated type](@ref).

The result is an `Hermitian` matrix.

(2) *Logarithmic map* (1) at base-point $G$ at once for $k$ positive definite matrices in 1d array $𝐏={P_1,...,P_k}$ of [ℍVector type](@ref).

The result is an `ℍVector`.

!!! note "Nota Bene"
    Currently only the [Fisher](@ref) metric is supported for tangent space operations.


The inverse operation is [`expMap`](@ref).

**See also**: [`vecP`](@ref), [`parallelTransport`](@ref).

**Examples**

```julia
using PosDefManifold
(1)
P=randP(3)
Q=randP(3)
metric=Fisher
G=mean(metric, P, Q)
# projecting P at the base point given by the geometric mean of P and Q
S=logMap(metric, P, G)

(2)
Pset=randP(3, 4)
# projecting all matrices in Pset at the base point given by their geometric mean.
Sset=logMap(Fisher, Pset, mean(Fisher, Pset))
```
