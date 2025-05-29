```julia
    (1) expMap(metric::Metric, S::ℍ{T}, G::ℍ{T})

    (2) expMap(metric::Metric, 𝐒::ℍVector, G::ℍ{T})
    for all the above: where T<:RealOrComplex
```

(1) *Exponential Map:* map a tangent vector (a matrix) $S$ from the tangent space at base-point $G$ into the SPD or Hermitian manifold (using the [Fisher](@ref) metric).

$S$ and $G$ must be flagged as `Hermitian`. See [typecasting matrices](@ref).

The map is defined as

$Exp_G(S)=P=G^{1/2}\textrm{exp}\big(G^{-1/2}SG^{-1/2}\big)G^{1/2}$.

`metric` is a metric of type [Metric::Enumerated type](@ref).

The result is an `Hermitian` matrix.

(2) *Exponential map* (1) at base-point $G$ at once for $k$ tangent vectors (matrices) in 1d array $𝐒={S_1,...,S_k}$ of [ℍVector type](@ref).

The result is an `ℍVector`.

!!! note "Nota Bene"
    Currently only the [Fisher](@ref) metric is supported for tangent space operations.


The inverse operation is [`logMap`](@ref).

**Examples**

```julia
(1)
using PosDefManifold, LinearAlgebra
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)
# projecting P on the tangent space at the Fisher mean base point G
S=logMap(Fisher, P, G)
# projecting back onto the manifold
P2=expMap(Fisher, S, G)

(2)
Pset=randP(3, 4)
# projecting all matrices in Pset at the base point given by their geometric mean.
G=mean(Fisher, Pset)
Sset=logMap(Fisher, Pset, G)
# projecting back onto the manifold
Pset2=expMap(Fisher, Sset, G)
```
