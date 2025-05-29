```
evd(S::Union{𝕄{T}, ℍ{T}}) where T<:RealOrComplex
```

Given a positive semi-definite matrix $S$,  returns a 2-tuple $(Λ, U)$, where $U$ is the matrix holding in columns  the eigenvectors and $Λ$ is the matrix holding the eigenvalues on the diagonal.  This is the output of Julia  [eigen](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.eigen)  function in $UΛU'=S$ form.

As for the `eigen` function, the eigenvalues and associated  eigenvectors are sorted by increasing values of eigenvalues.

$S$ may be real or complex and may be flagged by Julia as `Hermitian`  (in this case **PosDefManifold** assumes it is positive definite).

See [typecasting matrices](@ref).

**See also**: [`spectralFunctions`](@ref).

**Examples**

```julia
using PosDefManifold
A=randn(3, 3);
S=A+A';
Λ, U=evd(S); # which is equivalent to (Λ, U)=evd(P)
(U*Λ*U') ≈ S ? println(" ⭐ ") : println(" ⛔ ")
# => UΛU'=S, UΛ=SU, ΛU'=U'S
```
