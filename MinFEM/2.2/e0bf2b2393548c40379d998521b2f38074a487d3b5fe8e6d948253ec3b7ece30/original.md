```
twonorm(
    v::AbstractVector{Float64},
    mesh::Mesh; 
    qdim::Int64 = 1,
    order::Int64 = 3
)
```

Same as previous twonorm(...), but takes mesh and number of components as arguments. Then assembles the mass matrix and passes it to the base function.
