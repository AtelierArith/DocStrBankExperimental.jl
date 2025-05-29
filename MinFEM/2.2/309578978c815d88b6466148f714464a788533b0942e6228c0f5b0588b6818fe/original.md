```
assemble_cubicsecondderivativematrix(
    mesh::Mesh,
    y::AbstractVector,
    p::AbstractVector;
    order::Int64 = 3
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the second derivative of the cubic term  of the standard semilinear elliptic equation around the state y.
