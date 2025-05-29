```
compute_prolongation_zero(
    g::AbstractVector{Float64},
    mesh::Mesh;
    qdim::Int64 = 1
) -> AbstractVector{Float64}
```

Returns discrete prolongation of g to the whole domain by zero on every node.

Returns discrete prolongation of the boundary condition g to the whole domain by zero on every node.

# Mandatory Arguments

  * `g::AbstractVector{Float64}`: Discretely evaluated boundary condition.
  * `mesh::Mesh`: Mesh of the domain.

# Keyword Arguments

  * `qdim::Int64 = 1`: Number of components of f, h and g.
