```
invfrf(P::ℍ{T}) where T<:RealOrComplex
```

Inverse of the full-rank factorization of `Hermitian` matrix `P`. It is given by

$F=D^{-1/2}U^H$,

where

$\textrm{EVD}(P)=UDU^{H}$

is the eigenvalue-eigenvector decomposition of `P`. It verifies

$FPF^H=I$,

thus $F$ is a whitening matrix.

**See also**: [`frf`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3)
F = invfrf(P)
F*P*F'≈I ? println(" ⭐ ") : println(" ⛔ ")
```
