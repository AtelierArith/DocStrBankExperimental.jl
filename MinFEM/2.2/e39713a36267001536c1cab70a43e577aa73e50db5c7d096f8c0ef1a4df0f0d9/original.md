```
assemble_cubicderivativematrix(
    mesh::Mesh,
    y::AbstractVector;
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the linearization of the cubic term of the standard semilinear elliptic equation.
