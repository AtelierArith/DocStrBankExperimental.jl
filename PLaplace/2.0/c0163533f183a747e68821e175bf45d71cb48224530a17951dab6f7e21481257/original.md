```
compute_prolongation_harmonic(
    g::AbstractVector{Float64},
    mesh::Mesh,
    has_sourceterm::Bool,
    f::AbstractVector{Float64}, 
    dirichlet_nodes::Set{Int64},
    has_neumannboundary::Bool,
    h::AbstractVector{Float64},
    neumann_elements::Set{Int64}, 
    solveLS::Function,
    preconditioner::Function;
    qdim::Int64 = 1
) -> AbstractVector{Float64}
```

Returns discrete prolongation of the boundary condition g to the whole domain as solution of the corresponding linear Laplace problem, i.e. $p = 2$.

# Mandatory Arguments

  * `g::AbstractVector{Float64}`: Discretely evaluated boundary condition.
  * `mesh::Mesh`: Mesh of the domain.
  * `has_sourceterm::Bool`: Flag for evaluating source term.
  * `f::AbstractVector{Float64}`: Source term.
  * `dirichlet_nodes::Set{Int64}`: Nodes of the boundary to hold Dirichlet condition.
  * `has_neumannboundary::Bool`: Flag for evaluating Neumann boundary.
  * `h::AbstractVector{Float64}`: Neumann boundary condition.
  * `neumann_elements::Set{Int64}`: Edges of the boundary to hold Neumann condition.
  * `solveLS::Function`: Function pointer to solve linear system.
  * `preconditioner::Function`: Function pointer to compute preconditioner for linear system.

# Keyword Arguments

  * `qdim::Int64 = 1`: Number of components of f, h and g.
