```
(1) function dim(X::AnyMatrix, [d])
(2) function dim(vector::AnyMatrixVector, [d])
(3) function dim(vector₂::AnyMatrixVector₂, [d])
```

(1) $X$ is a real or complex `Matrix`, `Diagonal`,  `LowerTriangular` or `Hermitian` matrix.  Return a 2-tuple containing the dimensions of $X$,  which is two times the same dimension for all possible types of $X$  with the exception of the `Matrix` type, which can be rectangular.  Optionally you can specify a dimension (1 or 2)  to get just the length of that dimension.

(2) `vector` is an 𝕄Vector, 𝔻Vector, 𝕃Vector or ℍVector type  (see [AnyMatrixVector type](@ref)).  Return a 3-tuple containing the number of matrices it holds  (dimension 1) and their dimensions (dimension 2 and 3).  Optionally you can specify a dimension (1, 2, or 3)  to get just the length of that dimension.

(3) `vector₂` is an 𝕄Vector₂, 𝔻Vector₂, 𝕃Vector₂ or ℍVector₂ type  (see [AnyMatrixVector type](@ref)).  Return a 4-tuple containing

  * the number of vectors of matrices it holds (dimension 1),
  * a vector holding the number of matrices in each vector of matrices (dimensions 2),
  * the two dimensions of the matrices (dimension 3 and 4).

Optionally you can specify a dimension (1, 2, 3 or 4)  to get just the length of that dimension.

`vector` and `vector₂` are [Array of Matrices types](@ref).  See also [aliases](@ref) for the symbols `ℍ`, `𝔻`, `𝕃` and `𝕄`.

!!! note "Nota Bene"
    If you specify a dimension and this is out of the valid range, the function returns zero.

    Both the `vector`(2) and the `vector₂`(3) object are meant to hold matrices living in the same manifold, therefore it is assumed that all matrices they holds are of the same dimension. The dimensions of the matrices are retrived from

      * the first matrix in `vector`(2),
      * the first matrix in the first vector of `vector₂`(3).


This function replaces Julia [size](https://docs.julialang.org/en/v1/base/arrays/#Base.size)  function, which cannot be used to retrive dimension for matrix vectors.  It is not possible to overload the `size` function for matrix vectors  since this causes problems to other Julia functions.

**Examples**

```julia
using LinearAlgebra, PosDefManifold
# (1)
M=randn(3, 4) # generate a 3x4 `Matrix`
dim(M) # returns (3, 4)
dim(M, 1) # returns 3
dim(M, 2) # returns 4
dim(M, 3) # out of range: returns 0

# (2)
Pset=randP(3, 4) # generate an ℍVector holding 4 3x3 Hermitian matrices
dim(Pset) # returns (4, 3, 3)
dim(Pset, 1) # returns 4
dim(Pset, 2) # returns 3
dim(Pset, 3) # returns 3

# (3)
# Generate a set of 4 random 3x3 SPD matrices
Pset=randP(3, 4)
# Generate a set of 40 random 4x4 SPD matrices
Qset=randP(3, 40)
A=ℍVector₂([Pset, Qset])
dim(A) # return (2, [4, 40], 3, 3)
dim(A, 1) # return 2
dim(A, 2) # return [4, 40]
dim(A, 2)[1] # return 4
dim(A, 3) # return 3
dim(A, 4) # return 3
dim(A, 5) # out of range: return 0

# note: to create an ℍVector₂ object holding k ℍVector objects use
sets=ℍVector₂(undef, k) # and then fill them
```
