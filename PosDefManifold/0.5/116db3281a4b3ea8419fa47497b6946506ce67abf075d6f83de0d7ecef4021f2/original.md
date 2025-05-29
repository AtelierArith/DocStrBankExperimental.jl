```julia
    (1) parallelTransport(S::ℍ{T}, P::ℍ{T}, Q::ℍ{T})

    (2) parallelTransport(S::ℍ{T}, P::ℍ{T})

    (3) parallelTransport(𝐒::ℍVector, P::ℍ{T}, Q::ℍ{T})

    (4) parallelTransport(𝐒::ℍVector, P::ℍ{T})
    for all the above: where T<:RealOrComplex
```

**alias**: `pt`

(1) *Parallel transport* of tangent vector $S$ (a matrix) lying on the tangent space at base-point $P$ to the tangent space at base-point $Q$.

$S$, $P$ and $Q$ must all be `Hermitian` matrices. Return an `Hermitian` matrix. The transport is defined as:

$∥_{(P→Q)}(S)=\big(QP^{-1}\big)^{1/2}S\big(QP^{-1}\big)^{H/2}$.

If $S$ is a positive definite matrix in the manifold (and not a tangent vector) it will be 'trasported' from $P$ to $Q$, amounting to (Yair et *al.*, 2019[🎓](@ref))

  * project $S$ onto the tangent space at base-point $P$,
  * parallel transport it to the tangent space at base-point $Q$,
  * project it back onto the manifold at base-point $Q$.

(2) *Parallel transport* as in (1), but to the tangent space at base-point the *identity matrix*.

The transport reduces in this case to:

$∥_{(P→I)}(S)=P^{-1/2}SP^{-1/2}$.

(3) *Parallel transport* as in (1) at once for $k$ tangent vectors (matrices) in 1d array $𝐒={S_1,...,S_k}$ of [ℍVector type](@ref).

(4) *Parallel transport* as in (2) at once for $k$ tangent vectors (matrices) in 1d array $𝐒={S_1,...,S_k}$ of [ℍVector type](@ref).

!!! note "Nota Bene"
    Currently only the [Fisher](@ref) metric is supported for parallel transport.


**See also**: [`logMap`](@ref), [`expMap`](@ref), [`vecP`](@ref), [`matP`](@ref).

**Examples**

```julia
using PosDefManifold

(1)
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)

# i. projecting P onto the tangent space at base-point G
S=logMap(Fisher, P, G)
# ii. parallel transport S to the tangent space at base-point Q
S_=parallelTransport(S, G, Q)
# iii. projecting back into the manifold at base-point Q
P_=expMap(Fisher, S_, Q)

# i., ii. and iii. can be done simply by
PP_=parallelTransport(P, G, Q)
# check
P_≈PP_ ? println(" ⭐ ") : println(" ⛔ ")

(2)
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)
# transport to the tangent space at base-point the identity
PP_=parallelTransport(P, G)

(3)
Pset=randP(3, 4)
Q=randP(3)
G=mean(Fisher, Pset)
# trasport at once all matrices in Pset
Pset2=parallelTransport(Pset, G, Q)

(4)
Pset=randP(3, 4)
G=mean(Fisher, Pset)
# recenter all matrices so to have mean=I
Pset2=parallelTransport(Pset, G)
# check
mean(Fisher, Pset2) ≈ I ? println(" ⭐ ") : println(" ⛔ ")
```
