```
PoissonsEquation
```

A struct for defining a problem representing a (generalised) Poisson's equation:

$$
\div[D(\vb x)\grad u] = f(\vb x)
$$

inside a domain $\Omega$. See also [`LaplacesEquation`](@ref), a special case of this  problem with $f(\vb x) = 0$.

You can solve this problem using [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)).

# Constructor

```
PoissonsEquation(mesh::FVMGeometry,
    BCs::BoundaryConditions,
    ICs::InternalConditions=InternalConditions();
    diffusion_function=(x,y,p)->1.0,
    diffusion_parameters=nothing,
    source_function, 
    source_parameters=nothing,
    kwargs...)
```

## Arguments

  * `mesh::FVMGeometry`: The [`FVMGeometry`](@ref).
  * `BCs::BoundaryConditions`: The [`BoundaryConditions`](@ref). For these boundary conditions, all functions should still be of the form `(x, y, t, u, p) -> Number`, but the `t` and `u` arguments should be unused as they will be replaced with `nothing`.
  * `ICs::InternalConditions=InternalConditions()`: The [`InternalConditions`](@ref). For these internal conditions, all functions should still be of the form `(x, y, t, u, p) -> Number`, but the `t` and `u` arguments should be unused as they will be replaced with `nothing`.

## Keyword Arguments

  * `diffusion_function=(x,y,p)->1.0`: The diffusion function. Should be of the form `(x, y, p) -> Number`, where `p = diffusion_parameters` below.
  * `diffusion_parameters=nothing`: The argument `p` in `diffusion_function`.
  * `source_function`: The source function. Should be of the form `(x, y, p) -> Number`, where `p = source_parameters` below.
  * `source_parameters=nothing`: The argument `p` in `source_function`.
  * `kwargs...`: Any other keyword arguments are passed to the `LinearProblem` (from LinearSolve.jl) that represents the problem.

# Fields

The struct has extra fields in addition to the arguments above:

  * `A`: This is a sparse matrix `A` so that `Au = b`.
  * `b`: The `b` above.
  * `problem`: The `LinearProblem` that represents the problem. This is the problem that is solved when you call [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) on the struct.
