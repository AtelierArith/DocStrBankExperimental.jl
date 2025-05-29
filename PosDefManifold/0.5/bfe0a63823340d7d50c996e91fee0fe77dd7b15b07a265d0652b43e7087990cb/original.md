```
function det1(X::AnyMatrix; <tol::Real=0.>)
```

Return the argument matrix $X$ normalized so as to have *unit determinant*.  For square positive definite matrices this is the best approximant  from the set of matrices in the [special linear group](https://bit.ly/2W5jDZ6) -  see Bhatia and Jain (2014)[🎓](@ref).

$X$ can be a real or complex `Diagonal`, `LowerTriangular`,  `Matrix`, or `Hermitian` matrix. (see [AnyMatrix type](@ref))

If the determinant is not greater than `tol` (which defalts to zero)  a warning is printed and $X$ is returned.

!!! note "Nota Bene"
    This function is meant for positive definite matrices. Julia may throws an error while computing the determinant if the matrix is defective.


**See** [Julia det function](https://bit.ly/2Y4MnTF).

**See also**: [`tr1`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(5) # generate a random real positive definite matrix 5x5
Q=det1(P)
det(Q) # must be 1
# using a tolerance
Q=det1(P; tol=1e-12)
```
