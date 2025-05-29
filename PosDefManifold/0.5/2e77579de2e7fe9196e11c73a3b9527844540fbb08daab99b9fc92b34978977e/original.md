```
(1) pow(P::ℍ{T}, args...) where T<:RealOrComplex
(2) pow(D::𝔻{S}, args...) where S<:Real
```

(1) Given a positive semi-definite `Hermitian` matrix $P$, return the power  $P^{r_1}, P^{r_2},...$  for any number of exponents $r_1, r_2,...$.  It returns a tuple comprising as many elements as arguments passed after $P$.

$P$ must be flagged as `Hermitian`. See [typecasting matrices](@ref).

$arg1, arg2,...$ are real numbers.

A special method is provided for real `Diagonal` matrices (2).

**See also**: [`invsqrt`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(5);     # use P=randP(ComplexF64, 5) for generating an Hermitian matrix
Q=pow(P, 0.5);            # =>  QQ=P
Q, W=pow(P, 0.5, -0.5);
W*P*W ≈ I ? println(" ⭐ ") : println(" ⛔ ")
Q*Q ≈ P ? println(" ⭐ ") : println(" ⛔ ")
R, S=pow(P, 0.3, 0.7);
R*S ≈ P ? println(" ⭐ ") : println(" ⛔ ")
```
