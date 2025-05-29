Solve 2D Poisson's equation using the finite element method (FEM).

# Arguments

  * `N::Int`: Number of grid points along each dimension (excluding boundaries).
  * `f::Function`: A function representing the source term.
  * `Δx::Float64`: Spatial step size.

# Returns

  * `u::Array{Float64,2}`: The final solution field.
