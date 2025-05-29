```
(1) choL(P::ℍ{T}) where T<:RealOrComplex
(2) choL(D::𝔻{S}) where S<:Real
```

(1) Given a real or complex positive definite `Hermitian` matrix $P$,  return the *Cholesky lower triangular factor* $L$  such that $LL^H=P$. To obtain $L^H$ or both $L$ and $L^H$, use instead  julia function [cholesky](https://bit.ly/2u9Hw5P).

On output, $L$ is of type [`LowerTriangular`](https://bit.ly/2U511f3).

(2) For a real `Diagonal` matrix $D$, return $D^{1/2}$.

**See also**: [`choInv`](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(5);
L=choL(P);
L*L'≈ P ? println(" ⭐ ") : println(" ⛔ ")
```
