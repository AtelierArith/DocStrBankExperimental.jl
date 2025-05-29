Nelder-Mead method for 2D and above solvers

```julia
mutable struct NelderMeadMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# Fields

  * `N::Int64`: Number of parameters to optimize
  * `x_inis::Vector{FT} where FT<:AbstractFloat`: Initial values
  * `simplex::Array{Vector{FT}, 1} where FT<:AbstractFloat`: Simplex vector of vector with dimension (N+1) * (N+1)
  * `cen_x::Vector{FT} where FT<:AbstractFloat`: Centroid
  * `ref_x::Vector{FT} where FT<:AbstractFloat`: Reflection
  * `exp_x::Vector{FT} where FT<:AbstractFloat`: Expansion
  * `con_x::Vector{FT} where FT<:AbstractFloat`: Contraction
  * `history::Array{Vector{FT}, 1} where FT<:AbstractFloat`: history of all simulations
