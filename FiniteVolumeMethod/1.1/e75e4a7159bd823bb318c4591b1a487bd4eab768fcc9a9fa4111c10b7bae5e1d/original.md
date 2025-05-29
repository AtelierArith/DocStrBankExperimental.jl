```
LinearReactionDiffusionEquation
```

A struct for defining a problem representing a linear reaction-diffusion equation:

$$
\pdv{u}{t} = \div\left[D(\vb x)\grad u\right] + f(\vb x)u
$$

inside a domain $\Omega$. 

You can solve this problem using [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)).

!!! warning
    The solution to this problem will have an extra component added to it. The original solution will be inside  `sol[begin:end-1, :]`, where `sol` is the solution returned by [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)).


# Constructor

```
LinearReactionDiffusionEquation(mesh::FVMGeometry,
    BCs::BoundaryConditions,
    ICs::InternalConditions=InternalConditions();
    diffusion_function,
    diffusion_parameters=nothing,
    source_function,
    source_parameters=nothing,
    initial_condition,
    initial_time=0.0,
    final_time,
    kwargs...)
```

## Arguments

  * `mesh::FVMGeometry`: The [`FVMGeometry`](@ref).
  * `BCs::BoundaryConditions`: The [`BoundaryConditions`](@ref). For these boundary conditions, all functions should still be of the form `(x, y, t, u, p) -> Number`, but the `t` and `u` arguments should be unused as they will be replaced with `nothing`.
  * `ICs::InternalConditions=InternalConditions()`: The [`InternalConditions`](@ref). For these internal conditions, all functions should still be of the form `(x, y, t, u, p) -> Number`, but the `t` and `u` arguments should be unused as they will be replaced with `nothing`.

## Keyword Arguments

  * `diffusion_function`: The diffusion function. Should be of the form `(x, y, p) -> Number`, where `p = diffusion_parameters` below.
  * `diffusion_parameters=nothing`: The argument `p` in `diffusion_function`.
  * `source_function`: The source function. Should be of the form `(x, y, p) -> Number`, where `p = source_parameters` below.
  * `source_parameters=nothing`: The argument `p` in `source_function`.
  * `initial_condition`: The initial condition.
  * `initial_time=0.0`: The initial time.
  * `final_time`: The final time.
  * `kwargs...`: Any other keyword arguments are passed to the `ODEProblem` (from DifferentialEquations.jl) that represents the problem.

# Fields

The struct has extra fields in addition to the arguments above:

  * `A`: This is a sparse matrix `A` so that `du/dt = Au + b`.
  * `b`: The `b` above.
  * `Aop`: The `MatrixOperator` that represents the system so that `du/dt = Aop*u` (with `u` padded with an extra component since `A` is now inside `Aop`).
  * `problem`: The `ODEProblem` that represents the problem. This is the problem that is solved when you call [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) on the struct.
