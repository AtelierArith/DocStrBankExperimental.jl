```
(1) spectralFunctions(P::ℍ{T}, func) where T<:RealOrComplex
(2) spectralFunctions(D::𝔻{S}, func) where S<:Real
```

(1) This is the *mother function* for all spectral functions of eigenvalues implemented  in this library, which are:

  * `pow`     (power),
  * `isqrt`   (inverse square root).

The function `sqr` (square) does not use it, as it can be obtained more  efficiently by simple multiplication.

You can use this function if you need another spectral function of eigenvalues  besides those and those already implemented in the standard package `LinearAlgebra`.  In general, you won't call it directly.

`func` is the function that will be applied on the eigenvalues.

$P$ must be flagged as Hermitian. See [typecasting matrices](@ref).  It must be a positive definite or positive semi-definite matrix,  depending on `func`.

A special method is provided for real `Diagonal` matrices (2).

!!! note "Nota Bene"
    The function `func` must support the `func.` syntax and therefore must be able to apply element-wise to the eigenvalues (those include [anonymous functions](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions-1)).


### Maths

The definition of spectral functions for a positive definite matrix $P$  is at it follows:

$f\big(P\big)=Uf\big(Λ\big)U^H,$

where $U$ is the matrix holding in columns the eigenvectors of $P$,  $Λ$ is the matrix holding on diagonal its eigenvalues and $f$ is  a function applying element-wise to the eigenvalues.

**See also**: [`evd`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
n=5
P=randP(n) # P=randP(ComplexF64, 5) to generate an Hermitian complex matrix
noise=0.1;
Q=spectralFunctions(P, x->x+noise) # add white noise to the eigenvalues
tr(Q)-tr(P) ≈ noise*n ? println(" ⭐ ") : println(" ⛔ ")
```
