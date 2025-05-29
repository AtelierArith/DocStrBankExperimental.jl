```
frf(P::ℍ{T}) where T<:RealOrComplex
```

Full-rank factorization of `Hermitian` matrix `P`. It is given by

$F=UD^{1/2}$,

where

$\textrm{EVD}(P)=UDU^{H}$

is the eigenvalue-eigenvector decomposition of `P`. It verifies

$FF^H=P$,

thus $F^{-1}$ is a whitening matrix.

**See also**: [`invfrf`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3)
F = frf(P)
F*F'≈P ? println(" ⭐ ") : println(" ⛔ ")
```
