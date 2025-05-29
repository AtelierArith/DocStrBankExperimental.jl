```
(1) tr(P::ℍ{T}, Q::ℍ{T})
(2) tr(P::ℍ{T}, M::𝕄{T})
(3) tr(D::𝔻{T}, H::Union{ℍ{T}, 𝕄{T}})
(4) tr(H::Union{ℍ{T}, 𝕄{T}}, D::𝔻{T})
for all above: where T<:RealOrComplex
```

Given (1) two `Hermitian` positive definite matrix $P$ and $Q$,  return the trace of the product $PQ$.  This is real even if $P$ and $Q$ are complex.

$P$ must always be flagged as `Hermitian`. See [typecasting matrices](@ref).

In (2) $Q$ is a `Matrix` object,  in which case return

  * a real trace if the product $PQ$ is real or if it has all positive real eigenvalues.
  * a complex trace if the product $PQ$ is not real and has complex eigenvalues.

Methods (3) and (4) return the trace of the product $DH$ or $HD$,  where $D$ is a `Diagonal` matrix and $H$ an $Hermitian$  or $Matrix$ object. The result is of the same type as the input matrices.

For all methods all arguments must be of the same type.

## Math

Let $P$ and $Q$ be `Hermitian` matrices, using the properties of the trace  (e.g., the cyclic property and the similarity invariance) you can use this  function to fast compute the trace of several expressions. For example:

$\textrm{tr}(PQ)=\textrm{tr}(P^{1/2}QP^{1/2})$

and

$\textrm{tr}(PQP)=\textrm{tr}(P^{2}Q)$ (see example below).

**See**: [trace](https://bit.ly/2HoOLiM).

**See also**: [`DiagOfProd`](@ref), [`tr1`](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(ComplexF64, 5) # generate a random complex positive definite matrix 5x5
Q=randP(ComplexF64, 5) # generate a random complex positive definite matrix 5x5
tr(P, Q) ≈ tr(P*Q) ? println(" ⭐ ") : println(" ⛔ ")
tr(P, Q) ≈ tr(sqrt(P)*Q*sqrt(P)) ? println(" ⭐ ") : println(" ⛔ ")
tr(sqr(P), Q) ≈ tr(P*Q*P) ? println(" ⭐ ") : println(" ⛔ ")
```
