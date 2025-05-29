```
nearestPosDef(X::Union{𝔻, 𝕄}; tol::Real=0.)
```

Return the nearest symmetric/Hermitian positive semi-definite matrix  of a diagonal or of an arbitary square matrix `X` according to the  Frobenius norm.  If the eigenvalues of the symmetric part of `X` are all non-negative,  the result is positive definite and will be flagged as `Hermitian`,  otherwise it is positive semi-definite and will not be flagged.  The nearest matrix is given by

$(Y+H)/2$

where

$Y=(X+X^H)/2$

is the symmetric part of $X$, and $H$ is the symmetric polar factor  of $Y$. See Higham(1988)[🎓](@ref) for details and for the way it is computed.

**See also**: [`det1`](@ref), [`procrustes`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
X=randn(5, 5) # generate an arbitrary 5x5 matrix
S=nearestPosDef(X)

P=randP(5) # generate a random real positive definite 5x5 matrix
S=nearestPosDef(Matrix(P)) # typecasting an Hermitian matrix as a `Matrix`
# Since P is a positive definite matrix S must be equal to P
S ≈ P ? println(" ⭐ ") : println(" ⛔ ")
```
