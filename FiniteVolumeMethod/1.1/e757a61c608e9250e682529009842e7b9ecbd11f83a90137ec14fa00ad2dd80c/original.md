```
MeanExitTimeProblem
```

A struct for defining a problem representing a mean exit time problem:

$$
\div\left[D(\vb x)\grad T\right] =-1
$$

inside a domain $\Omega$. This problem is a special case of [`PoissonsEquation`](@ref), but is defined separately since it is common enough to warrant its own definition; `MeanExitTimeProblem` is constructed using [`PoissonsEquation`](@ref).

You can solve this problem using [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)).

# Constructor

```
MeanExitTimeProblem(mesh::FVMGeometry,
    BCs::BoundaryConditions,
    ICs::InternalConditions=InternalConditions();
    diffusion_function,
    diffusion_parameters=nothing,
    kwargs...)
```

## Arguments

  * `mesh::FVMGeometry`: The [`FVMGeometry`](@ref).
  * `BCs::BoundaryConditions`: The [`BoundaryConditions`](@ref).
  * `ICs::InternalConditions=InternalConditions()`: The [`InternalConditions`](@ref).

The functions for `BCs` and `ICs` are not used. Whenever a [`Neumann`](@ref) condition is encountered,  or a [`Dirichlet`](@ref) condition, it is assumed that the conditon is homogeneous. If any of the  conditions are [`Dudt`](@ref) or [`Constrained`](@ref) types, then an error is thrown.

## Keyword Arguments

  * `diffusion_function`: The diffusion function. Should be of the form `(x, y, p) -> Number`, where `p = diffusion_parameters` below.
  * `diffusion_parameters=nothing`: The argument `p` in `diffusion_function`.
  * `kwargs...`: Any other keyword arguments are passed to the `LinearProblem` (from LinearSolve.jl) that represents the problem.

# Fields

The struct has extra fields in addition to the arguments above:

  * `A`: This is a sparse matrix `A` so that `AT = b`.
  * `b`: The `b` above.
  * `problem`: The `LinearProblem` that represents the problem. This is the problem that is solved when you call [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) on the struct.
