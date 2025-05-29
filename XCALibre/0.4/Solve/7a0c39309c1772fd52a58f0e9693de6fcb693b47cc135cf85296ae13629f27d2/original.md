```
set_solver( 
    field::AbstractField;
    # keyword arguments and defaults
    solver::S, 
    preconditioner::PT, 
    convergence, 
    relax,
    smoother=nothing,
    limit=(),
    itmax::Integer=1000, 
    atol=(eps(_get_float(field.mesh)))^0.9,
    rtol=_get_float(field.mesh)(1e-1)
    ) where {S,PT<:PreconditionerType} = begin

    # return NamedTuple
    TF = _get_float(field.mesh)
    (
        solver=solver, 
        preconditioner=preconditioner, 
        convergence=convergence |> TF, 
        relax=relax |> TF, 
        smoother=smoother,
        limit=limit,
        itmax=itmax, 
        atol=atol |> TF, 
        rtol=rtol |> TF
    )
end
```

This function is used to provide solver settings that will be used internally in XCALibre.jl. It returns a `NamedTuple` with solver settings that are used internally by the flow solvers. 

# Input arguments

  * `field` reference to the field to which the solver settings will apply (used to provide integer and float types required)
  * `solver` solver object from Krylov.jl and it could be one of `BicgstabSolver`, `CgSolver`, `GmresSolver` which are re-exported in XCALibre.jl
  * `preconditioner` instance of preconditioner to be used e.g. Jacobi()
  * `convergence` sets the stopping criteria of this field
  * `relax` specifies the relaxation factor to be used e.g. set to 1 for no relaxation
  * `smoother` specifies smoothing method to be applied before discretisation. `JacobiSmoother` is currently the only choice (defaults to `nothing`)
  * `limit` used in some solvers to bound the solution within this limits e.g. (min, max). It defaults to `()`
  * `itmax` maximum number of iterations in a single solver pass (defaults to 1000)
  * `atol` absolute tolerance for the solver (default to eps(FloatType)^0.9)
  * `rtol` set relative tolerance for the solver (defaults to 1e-1)
