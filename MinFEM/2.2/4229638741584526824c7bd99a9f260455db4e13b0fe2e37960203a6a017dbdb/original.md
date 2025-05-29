```julia
mutable struct PDESystem
```

Structure holding all information to describe simple PDEs  with Dirichlet boundary conditions.

# Fields

  * `A::SparseArrays.SparseMatrixCSC{Float64, Int64}`: Stiffness matrix
  * `b::Vector{Float64}`: Load vector
  * `bc::Vector{Float64}`: Dirichlet boundary values
  * `DI::Set{Int64}`: Dirichlet nodes
  * `qdim::Int64`: Components of vector-valued state
  * `Factors::Any`: System matrix factorization
  * `SystemMatrix::SparseArrays.SparseMatrixCSC{Float64, Int64}`: System of stiffness matrix and Dirichlet conditinons
  * `B::SparseArrays.SparseMatrixCSC{Float64, Int64}`: Dirichlet projection matrix
  * `state::Vector{Float64}`: Solution vector
  * `rhs::Vector{Float64}`: Right hand side vector with source term and dirichlet conditions
