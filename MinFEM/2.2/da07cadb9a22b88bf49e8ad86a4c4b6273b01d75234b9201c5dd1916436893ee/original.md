```
assemble_cubicterm(
    mesh::Mesh,
    y::AbstractVector;
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the cubic term of the standard semilinear parabolic equation.
