```
AlmostBlockDiagonal{T, I <: Integer, V <: AbstractMatrix{T}} <: AbstractMatrix{T}
```

A matrix with block matrices on the diagonal, but not strictly has their corner against each other.

For example:

A 10 x 10 matrix:

x  x  x  x x  x  x  x x  x  x  x       x  x  x  x       x  x  x  x             x  x  x  x             x  x  x  x                   x  x  x  x                   x  x  x  x                   x  x  x  x

can be abstracted as:

```julia
julia> AlmostBlockDiagonal([rand(3,4),rand(2,4),rand(2,4),rand(3,4)], [2,2,2,4])
```

Here, the first argument is the fillers in the almost block diagonal matrix, the second argument is the offset of each adjacent block in the diagonal.

! note     The column of block `ncol` and row of block `nrow` must satisfy: `ncol` ≥ `nrow`.

The implementation mainly comes from the paper: [SOLVEBLOK: A Package for Solving Almost Block Diagonal Linear Systems](https://dl.acm.org/doi/pdf/10.1145/355873.355880) which is originally a FORTRAN program for the solution of an almost block diagonal system by gaussian elimination with scale row pivoting.
