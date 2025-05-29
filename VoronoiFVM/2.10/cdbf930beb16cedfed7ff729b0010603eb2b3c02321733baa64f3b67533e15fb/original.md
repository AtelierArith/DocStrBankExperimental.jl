```julia
mutable struct System{Tv, Tc, Ti, Tm, TSpecMat<:(AbstractMatrix)} <: VoronoiFVM.AbstractSystem{Tv, Tc, Ti, Tm}
```

Structure holding data for finite volume system.

Subtype of [`AbstractSystem`](@ref).

Type parameters:

  * TSpecMat: Type of matrix storing species information (Matrix or SparseMatrixCSC)

For the other type parameters, see [`AbstractSystem`](@ref).

  * `grid::ExtendableGrids.ExtendableGrid`: Grid

  * `physics::VoronoiFVM.Physics`: Physics data

  * `boundary_values::Matrix`: Array of boundary condition values

  * `boundary_factors::Matrix`: Array of boundary condition factors

  * `region_species::AbstractMatrix`: Matrix containing species numbers for inner regions

  * `bregion_species::AbstractMatrix`: Matrix containing species numbers for boundary regions

  * `node_dof::AbstractMatrix`: Matrix containing degree of freedom numbers for each node

  * `matrixtype::Symbol`: - :multidiagonal  (currently disabled)

      * :sparse
      * :banded
      * :tridiagonal

  * `species_homogeneous::Bool`: Flag which says if the number of unknowns per node is constant

  * `num_quantities::Any`: Number of quantities defined on system

  * `num_parameters::Any`: Number of parameter the system depends on.

  * `assembly_data::Union{Nothing, VoronoiFVM.AbstractAssemblyData{Tc, Ti}} where {Tc, Ti}`: Precomputed form factors for bulk  assembly

  * `boundary_assembly_data::VoronoiFVM.AbstractAssemblyData`: Precomputed form factors for boundary assembly

  * `assembly_type::Symbol`: :edgewise or :cellwise

  * `is_linear::Bool`: Is the system linear ?

  * `outflownoderegions::Union{Nothing, SparseArrays.SparseMatrixCSC{Bool, Int64}}`: Outflow nodes with their region numbers.

  * `generic_matrix_prep::Any`: Sparse matrix colors etc. for generic operator handling

  * `generic_matrix_backend::Any`: Sparsity detector backend

  * `is_complete::Bool`: Has the system been completed (species information compiled)?
