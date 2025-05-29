```
tr1(X::AnyMatrix; tol::Real=0.)
```

Return the argument matrix $X$ normalized so as to have *unit trace*.

$X$ can be a real or complex `Diagonal`, `LowerTriangular`,  `Matrix` or `Hermitian` matrix (see [AnyMatrix type](@ref)).  Its trace must be real. If the absolute value of its imaginary part  is greater than `tol` (which defalts to zero) a warning is printed  and $X$ is returned.  Also, if the trace is not greater than `tol`  a warning is printed and $X$ is returned.

**See**: [Julia trace function](https://bit.ly/2HoOLiM).

**See also**: [`tr`](@ref), [`det1`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold

P=randP(5) # generate a random real positive definite matrix 5x5
Q=tr1(P)
tr(Q)  # must be 1
# using a tolerance
Q=tr1(P; tol=1e-12)

Pc=randP(ComplexF64, 5) # generate a random real positive definite matrix 5x5
Qc=tr1(Pc)
tr(Qc)  # must be 1
```
