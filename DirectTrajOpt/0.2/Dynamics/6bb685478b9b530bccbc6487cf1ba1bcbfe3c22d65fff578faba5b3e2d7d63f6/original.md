```
TrajectoryDynamics
```

A struct for trajectory optimization dynamics, represented by integrators that compute single time step dynamics, and functions for jacobians and hessians.

# Fields

  * `integrators::Union{Nothing, Vector{<:AbstractIntegrator}}`: Vector of integrators.
  * `F!::Function`: Function to compute trajectory dynamics.
  * `∂F!::Function`: Function to compute the Jacobian of the dynamics.
  * `∂fs::Vector{SparseMatrixCSC{Float64, Int}}`: Vector of Jacobian matrices.
  * `μ∂²F!::Union{Function, Nothing}`: Function to compute the Hessian of the Lagrangian.
  * `μ∂²fs::Vector{SparseMatrixCSC{Float64, Int}}`: Vector of Hessian matrices.
  * `dim::Int`: Total dimension of the dynamics.
