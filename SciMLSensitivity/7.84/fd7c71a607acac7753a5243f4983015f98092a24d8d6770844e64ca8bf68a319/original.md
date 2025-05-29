```julia
SteadyStateAdjoint{CS, AD, FDT, VJP, LS} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

An implementation of the adjoint differentiation of a nonlinear solve. Uses the implicit function theorem to directly compute the derivative of the solution to $f(u,p) = 0$ with respect to `p`.

## Constructor

```julia
SteadyStateAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = autodiff, linsolve = nothing)
```

## Keyword Arguments

  * `autodiff`: Use automatic differentiation for constructing the Jacobian if the Jacobian needs to be constructed.  Defaults to `true`.
  * `chunk_size`: Chunk size for forward-mode differentiation if full Jacobians are built (`autojacvec=false` and `autodiff=true`). Default is `0` for automatic choice of chunk size.
  * `diff_type`: The method used by FiniteDiff.jl for constructing the Jacobian if the full Jacobian is required with `autodiff=false`.
  * `autojacvec`: Calculate the vector-Jacobian product (`J'*v`) via automatic differentiation with special seeding. The total set of choices are:

      * `nothing`: uses an automatic algorithm to automatically choose the vjp. This is the default and recommended for most users.
      * `false`: the Jacobian is constructed via FiniteDiff.jl
      * `true`: the Jacobian is constructed via ForwardDiff.jl
      * `TrackerVJP`: Uses Tracker.jl for the vjp.
      * `ZygoteVJP`: Uses Zygote.jl for the vjp.
      * `EnzymeVJP`: Uses Enzyme.jl for the vjp.
      * `ReverseDiffVJP(compile=false)`: Uses ReverseDiff.jl for the vjp. `compile` is a boolean for whether to precompile the tape, which should only be done if there are no branches (`if` or `while` statements) in the `f` function.
  * `linsolve`: the linear solver used in the adjoint solve. Defaults to `nothing`, which uses a polyalgorithm to choose an efficient algorithm automatically.
  * `linsolve_kwargs`: keyword arguments to be passed to the linear solver.

For more details on the vjp choices, please consult the sensitivity algorithms documentation page or the docstrings of the vjp types.

## References

Johnson, S. G., Notes on Adjoint Methods for 18.336, Online at http://math.mit.edu/stevenj/18.336/adjoint.pdf (2007)
