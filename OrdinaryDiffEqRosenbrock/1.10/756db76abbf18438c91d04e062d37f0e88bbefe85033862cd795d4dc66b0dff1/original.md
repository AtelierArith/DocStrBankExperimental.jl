```julia
Rodas23W(; chunk_size = Val{0}(),
           standardtag = Val{true}(),
           autodiff = AutoForwardDiff(),
           concrete_jac = nothing,
           diff_type = Val{:forward}(),
           linsolve = nothing,
           precs = DEFAULT_PRECS,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!)
```

Rosenbrock-Wanner-W(olfbrandt) Method.  An Order 2/3 L-Stable Rosenbrock-W method for stiff ODEs and DAEs in mass matrix form. 2nd order stiff-aware interpolation and additional error test for interpolation.

### Keyword Arguments

  * `standardtag`: Specifies whether to use package-specific tags instead of the   ForwardDiff default function-specific tags. For more information, see   [this blog post](https://www.stochasticlifestyle.com/improved-forwarddiff-jl-stacktraces-with-package-tags/).   Defaults to `Val{true}()`.
  * `autodiff`: Uses [ADTypes.jl](https://sciml.github.io/ADTypes.jl/stable/)    to specify whether to use automatic differentiation via   [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) or finite   differencing via [FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl).    Defaults to `AutoForwardDiff()` for automatic differentiation, which by default uses   `chunksize = 0`, and thus uses the internal ForwardDiff.jl algorithm for the choice.   To use `FiniteDiff.jl`, the `AutoFiniteDiff()` ADType can be used, which has a keyword argument   `fdtype` with default value `Val{:forward}()`, and alternatives `Val{:central}()` and `Val{:complex}()`.
  * `concrete_jac`: Specifies whether a Jacobian should be constructed. Defaults to   `nothing`, which means it will be chosen true/false depending on circumstances   of the solver, such as whether a Krylov subspace method is used for `linsolve`.
  * `linsolve`: Any [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) compatible linear solver. For example, to use [KLU.jl](https://github.com/JuliaSparse/KLU.jl), specify `Rodas23W(linsolve = KLUFactorization()`).  When `nothing` is passed, uses `DefaultLinearSolver`.
  * `precs`: Any [LinearSolve.jl-compatible preconditioner](https://docs.sciml.ai/LinearSolve/stable/basics/Preconditioners/) can be used as a left or right preconditioner. Preconditioners are specified by the `Pl,Pr = precs(W,du,u,p,t,newW,Plprev,Prprev,solverdata)` function where the arguments are defined as:

      * `W`: the current Jacobian of the nonlinear system. Specified as either   $I - \gamma J$ or $I/\gamma - J$ depending on the algorithm. This will   commonly be a `WOperator` type defined by OrdinaryDiffEq.jl. It is a lazy   representation of the operator. Users can construct the W-matrix on demand   by calling `convert(AbstractMatrix,W)` to receive an `AbstractMatrix` matching   the `jac_prototype`.
      * `du`: the current ODE derivative
      * `u`: the current ODE state
      * `p`: the ODE parameters
      * `t`: the current ODE time
      * `newW`: a `Bool` which specifies whether the `W` matrix has been updated since   the last call to `precs`. It is recommended that this is checked to only   update the preconditioner when `newW == true`.
      * `Plprev`: the previous `Pl`.
      * `Prprev`: the previous `Pr`.
      * `solverdata`: Optional extra data the solvers can give to the `precs` function.   Solver-dependent and subject to change.

    The return is a tuple `(Pl,Pr)` of the LinearSolve.jl-compatible preconditioners. To specify one-sided preconditioning, simply return `nothing` for the preconditioner which is not used. Additionally, `precs` must supply the dispatch:

    ```julia
    Pl, Pr = precs(W, du, u, p, t, ::Nothing, ::Nothing, ::Nothing, solverdata)
    ```

    which is used in the solver setup phase to construct the integrator type with the preconditioners `(Pl,Pr)`. The default is `precs=DEFAULT_PRECS` where the default preconditioner function is defined as:

    ```julia
    DEFAULT_PRECS(W, du, u, p, t, newW, Plprev, Prprev, solverdata) = nothing, nothing
    ```
  * `step_limiter!`: function of the form `limiter!(u, integrator, p, t)`

## References

  * Steinebach G., Rosenbrock methods within OrdinaryDiffEq.jl - Overview, recent developments and applications - Preprint 2024 https://github.com/hbrs-cse/RosenbrockMethods/blob/main/paper/JuliaPaper.pdf
