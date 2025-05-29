```
(1) invsqrt(P{T}::ℍ) where T<:RealOrComplex
(2) invsqrt(D{S}::𝔻) where S<:Real
```

Given a positive definite `Hermitian` matrix $P$,  compute the inverse of the principal  square root $P^{-1/2}$.

$P$ must be flagged as Hermitian. See [typecasting matrices](@ref).

A special method is provided for real `Diagonal` matrices (2).

### Maths

The principal square root of a positive definite matrix $P$ is the only  symmetric (if $P$ is real) or Hermitian (if $P$ is complex) square root.  Its inverse $P^{-1/2}$ is also named the **whitening** or **sphering**  matrix since$P^{-1/2}PP^{-1/2}=I$.

**See**: [typecasting matrices](@ref).

**See also**: [`pow`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(ComplexF64, 5);
Q=invsqrt(P);
Q*P*Q ≈ I ? println(" ⭐ ") : println(" ⛔ ")
```
