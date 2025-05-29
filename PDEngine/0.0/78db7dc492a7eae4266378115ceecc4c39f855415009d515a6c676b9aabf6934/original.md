```
heat_crank_nicolson(N, α, T, Δx, Δt)
```

Solve the 1D heat equation using the Crank-Nicolson method.

# Arguments

  * `N::Int`: The number of spatial grid points (excluding boundary points).
  * `α::Float64`: The thermal diffusivity or the diffusion coefficient.
  * `T::Float64`: The total simulation time.
  * `Δx::Float64`: The spatial step size.
  * `Δt::Float64`: The time step size.

# Returns

  * `Vector{Float64}`: The temperature distribution at the final time step.
