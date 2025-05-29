Solve 2D Poisson's equation using the finite difference method.

# Arguments

  * `N::Int`: Number of grid points along each dimension (excluding boundaries).
  * `f::Array{Float64,2}`: A 2D array representing the source term on the grid.
  * `Δx::Float64`: Spatial step size.

# Returns

  * `u::Array{Float64,2}`: The final solution field.
