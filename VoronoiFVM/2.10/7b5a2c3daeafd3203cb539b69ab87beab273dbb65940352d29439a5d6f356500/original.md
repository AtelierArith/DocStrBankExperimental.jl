```julia
mutable struct SystemState{Tv, Tp, TMatrix<:AbstractArray{Tv, 2}, TGenericMatrix, TSolArray<:AbstractArray{Tv, 2}, TData}
```

Structure holding state information for finite volume system.

Type parameters:

  * Tv: element type of solution vectors and matrix
  * TMatrix:  matrix type
  * TSolArray: type of solution vector: (Matrix or SparseMatrixCSC)
  * TData: type of user data

Type fields:

  * `system::VoronoiFVM.System`: Related finite volume system

  * `data::Any`: User data

  * `solution::AbstractMatrix`: Solution vector

  * `matrix::AbstractMatrix`: Jacobi matrix for nonlinear problem

  * `generic_matrix::Any`: Sparse matrix for generic operator handling

  * `dudp::Vector{TSolArray} where {Tv, TSolArray<:AbstractMatrix{Tv}}`: Parameter derivative (vector of solution arrays)

  * `update::AbstractMatrix`: Vector holding Newton update

  * `residual::AbstractMatrix`: Vector holding Newton residual

  * `linear_cache::Union{Nothing, LinearSolve.LinearCache}`: Linear solver cache

  * `params::Vector`: Parameter vector

  * `uhash::UInt64`: Hash value of latest unknowns vector the assembly was called with (used by differential equation interface)

  * `history::Union{Nothing, VoronoiFVM.DiffEqHistory}`: History record for solution process (used by differential equation interface)
