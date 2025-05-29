```
FVMProblem(mesh, boundary_conditions[, internal_conditions];
    diffusion_function=nothing,
    diffusion_parameters=nothing,
    source_function=nothing,
    source_parameters=nothing,
    flux_function=nothing,
    flux_parameters=nothing,
    initial_condition,
    initial_time=0.0,
    final_time)
```

Constructs an `FVMProblem`. See also [`FVMSystem`](@ref) and [`SteadyFVMProblem`](@ref).

# Arguments

  * `mesh::FVMGeometry`

The mesh on which the PDE is defined, given as a [`FVMGeometry`](@ref).

  * `boundary_conditions::BoundaryConditions`

The boundary conditions for the PDE, given as a [`BoundaryConditions`](@ref).

  * `internal_conditions::InternalConditions=InternalConditions()`

The internal conditions for the PDE, given as an [`InternalConditions`](@ref). This argument  is optional.

# Keyword Arguments

  * `diffusion_function=nothing`

If `isnothing(flux_function)`, then this can be provided to give the diffusion-source formulation. See also [`construct_flux_function`](@ref). Should be of the form `D(x, y, t, u, p)`.

  * `diffusion_parameters=nothing`

The argument `p` for `diffusion_function`.

  * `source_function=(x, y, t, u, p) -> zero(u)`

The source term, given in the form `S(x, y, t, u, p)`.

  * `source_parameters=nothing`

The argument `p` for `source_function`.

  * `flux_function=nothing`

The flux function, given in the form `q(x, y, t, α, β, γ, p) ↦ (qx, qy)`, where `(qx, qy)` is the flux vector, `(α, β, γ)` are the shape function coefficients for estimating `u ≈ αx+βy+γ`. If `isnothing(flux_function)`, then `diffusion_function` is used instead to construct the function.

  * `flux_parameters=nothing`

The argument `p` for `flux_function`.

  * `initial_condition`

The initial condition, with `initial_condition[i]` the initial value at the `i`th node of the `mesh`.

  * `initial_time=0.0`

The initial time.

  * `final_time`

The final time.

# Outputs

The returned value is the corresponding [`FVMProblem`](@ref) struct. You can then solve the problem using [`solve(::Union{FVMProblem,FVMSystem}, ::Any; kwargs...)`](@ref) from DifferentialEquations.jl.
