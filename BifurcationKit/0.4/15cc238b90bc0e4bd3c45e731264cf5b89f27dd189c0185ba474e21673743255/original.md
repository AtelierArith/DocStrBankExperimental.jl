```julia
continuation(
    prob,
    alg,
    contparams;
    linear_algo,
    bothside,
    kwargs...
)

```

Compute the continuation curve associated to the functional `F` which is stored in the bifurcation problem `prob`. General information is available in [Continuation methods: introduction](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/IntroContinuation/).

# Arguments:

  * `prob::AbstractBifurcationFunction` a `::AbstractBifurcationProblem`, typically a  [`BifurcationProblem`](@ref) which holds the vector field and its jacobian. We also refer to  [`BifFunction`](@ref) for more details.
  * `alg` continuation algorithm, for example `Natural(), PALC(), Multiple(),...`. See [algos](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/Predictors/)
  * `contparams::ContinuationPar` parameters for continuation. See [`ContinuationPar`](@ref)

# Optional Arguments:

  * `plot = false` whether to plot the solution/branch/spectrum while computing the branch
  * `bothside = true` compute the branches on the two sides of the initial parameter value `p0`, merge them and return it.
  * `normC = norm` norm used in the nonlinear solves
  * `filename` to save the computed branch during continuation. The identifier .jld2 will be appended to this filename. This requires `using JLD2`.
  * `callback_newton` callback for newton iterations. See docs of [`newton`](@ref). For example, it can be used to change the preconditioners.
  * `finalise_solution = (z, tau, step, contResult; kwargs...) -> true` Function called at the end of each continuation step. Can be used to alter the continuation procedure (stop it by returning `false`), save personal data, plot... The notations are `z = BorderedArray(x, p)` where `x` (resp. `p`) is the current solution (resp. parameter value), `tau::BorderedArray` is the tangent at `z`, `step::Int` is the index of the current continuation step and `contResult` is the current branch. For advanced use:

      * the state `state::ContState` of the continuation iterator is passed in `kwargs`. This can be used for testing whether this is called from bisection for locating bifurcation points / events: `in_bisection(state)` for example. This allows to escape some personal code in this case.

    Note that you can have a better control over the continuation procedure by using an iterator, see [Iterator Interface](@ref).

      * the iterator `iter::ContIterable` of the continuation is passed in `kwargs`.
  * `verbosity::Int = 0` controls the amount of information printed during the continuation process. Must belong to `{0,1,2,3}`. In case `contparams.newton_options.verbose = false`, the following is valid (otherwise the newton iterations are shown). Each case prints more information than the previous one:

      * case 0: print nothing
      * case 1: print basic information about the continuation: used predictor, step size and parameter values
      * case 2: print newton iterations number, stability of solution, detected bifurcations / events
      * case 3: print information during bisection to locate bifurcations / events
  * `linear_algo` set the linear solver for the continuation algorithm `alg.` For example, `PALC` needs a linear solver for an enlarged problem (size `n+1` instead of `n`) and one thus needs to tune the one passed in `contparams.newton_options.linsolver`. This is a convenient argument to thus change the `alg` linear solver and is used mostly internally. The proper way is to pass directly to `alg` the correct linear solver.
  * `kind::AbstractContinuationKind` [Internal] flag to describe continuation kind (equilibrium, codim 2, ...). Default = `EquilibriumCont()`

# Output:

  * `contres::ContResult` composite type which contains the computed branch. See [`ContResult`](@ref) for more information.

!!! tip "Continuing the branch in the opposite direction"
    Just change the sign of `ds` in `ContinuationPar`.


!!! tip "Debug mode"
    Use debug mode to access more irformation about the progression of the continuation run, like iterative solvers convergence, problem update, ...

