```
(1) normalizeCol!(X::𝕄{T}, j::Int)
(2) normalizeCol!(X::𝕄{T}, j::Int, by::Number)
(3) normalizeCol!(X::𝕄{T}, range::UnitRange)
(4) normalizeCol!(X::𝕄{T}, range::UnitRange, by::Number)
for all above: where T<:RealOrComplex
```

Given a `Matrix` type $X$ comprised of real or complex elements,

  * (1) normalize the $j^{th}$ column to unit norm
  * (2) divide the elements of the $j^{th}$ column by number $by$
  * (3) normalize the columns in $range$ to unit norm
  * (4) divide the elements of columns in $range$  by number $by$.

$by$ is a number of abstract supertype [Number](https://bit.ly/2JwXjGr).  It should be an integer, real or complex number.  For efficiency, it should be of the same type as the elements of $X$.

$range$ is a [UnitRange](https://bit.ly/2HSfK5J) type.

Methods (1) and (3) call the  [BLAS.nrm2](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.nrm2)  routine for computing the norm of concerned columns.  See [Threads](@ref).

!!! note "Nota Bene"
    Julia does not allow normalizing the columns of `Hermitian` matrices. If you want to call this function for an `Hermitian` matrix see [typecasting matrices](@ref).


**See** [norm](https://bit.ly/2TaAkR0) and also [randn](https://bit.ly/2I1Vgrg)  for the example below.

**See also**: [`colNorm`](@ref), [`colProd`](@ref).

**Examples**

```julia
using PosDefManifold
X=randn(10, 20)
normalizeCol!(X, 2)                  # (1) normalize columns 2
normalizeCol!(X, 2, 10.0)            # (2) divide columns 2 by 10.0
normalizeCol!(X, 2:4)                # (3) normalize columns 2 to 4
X=randn(ComplexF64, 10, 20)
normalizeCol!(X, 3)                  # (1) normalize columns 3
normalizeCol!(X, 3:6, (2.0 + 0.5im)) # (4) divide columns 3 to 5 by (2.0 + 0.5im)
```
