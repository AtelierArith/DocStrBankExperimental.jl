```
fDiag(func::Function, X::AnyMatrix, k::Int=0)
```

**alias**: `𝑓𝔻`

Applies function `func` element-wise to the elements of the $k^{th}$  diagonal of real or complex `Diagonal`, `LowerTriangular`, `Matrix`  or `Hermitian` matrix $X$ and return a diagonal matrix with these elements.  $X$ must be square in all cases, but for the 𝕄=`Matrix` type argument,  in which case it may be of dimension *r⋅c*, with *r ≠ c*.

See julia [tril(M, k::Integer)](https://bit.ly/2Tbx8o7) function  for numbering of diagonals.

Bt default the main diagonal is considered.

  * If $X$ is `Diagonal`, $k$ is set automatically to zero (main diagonal).
  * If $X$ is `LowerTriangular`, $k$ cannot be positive.

Note that if $X$ is rectangular the dimension of the result depends  on the size of $X$ and on the chosen diagonal.  For example,

  * *r ≠ c* and $k$=0 (main diagonal), the result will be of dimension min*(r,c)*⋅*min(r,c)*,
  * $X$ *3⋅4* and $k=-1$, the result will be *2⋅2*,
  * $X$ *3⋅4* and $k=1$, the result will be *3⋅3*, etc.

!!! note "Nota Bene"
    The function `func` must support the `func.` syntax and therefore must be able to apply element-wise to the elements of the chosen diagonal (this includes [anonymous functions](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions-1)). If the input matrix is complex, the function `func` must be able to support complex arguments.


**See also**: [`DiagOfProd`](@ref), [`tr`](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(5) # use P=randP(ComplexF64, 5) for generating an Hermitian matrix

# diagonal matrix with the inverse of the first sub-diagonal of P
D=fDiag(inv, P, -1)

(Λ, U) = evd(P) # Λ holds the eigenvalues of P, see evd

# diagonal matrix with the log of the eigenvalues
Δ=fDiag(log, Λ)

# using an anonymous function for the square of the eigenvalues
Δ=fDiag(x->x^2, Λ)
```
