```julia
struct ShootingProblem{Tf<:BifurcationKit.AbstractFlow, Tjac<:BifurcationKit.AbstractJacobianType, Ts, Tsection, Tpar, Tlens} <: BifurcationKit.AbstractShootingProblem
```

Create a problem to implement the Simple / Parallel Multiple Standard Shooting method to locate periodic orbits. More details (maths, notations, linear systems) can be found [here](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitShooting/). The arguments are as described below.

A functional, hereby called `G`, encodes the shooting problem. For example, the following methods are available:

  * `pb(orbitguess, par)` evaluates the functional G on `orbitguess`
  * `pb(orbitguess, par, du)` evaluates the jacobian `dG(orbitguess)⋅du` functional at `orbitguess` on `du`.
  * `pb`(Val(:JacobianMatrixInplace), J, x, par)` compute the jacobian of the functional analytically. This is based on ForwardDiff.jl. Useful mainly for ODEs.
  * `pb(Val(:JacobianMatrix), x, par)` same as above but out-of-place.

You can then call `pb(orbitguess, par)` to apply the functional to a guess. Note that `orbitguess::AbstractVector` must be of size `M * N + 1` where N is the number of unknowns of the state space and `orbitguess[M * N + 1]` is an estimate of the period `T` of the limit cycle. This form of guess is convenient for the use of the linear solvers in `IterativeSolvers.jl` (for example) which only accept `AbstractVector`s. Another accepted guess is of the form `BorderedArray(guess, T)` where `guess[i]` is the state of the orbit at the `i`th time slice. This last form allows for non-vector state space which can be convenient for 2d problems for example, use `GMRESKrylovKit` for the linear solver in this case.

Note that you can generate this guess from a function solution using `generate_solution` or `generate_ci_problem`.

# Fields

  * `M::Int64`: `ds`: vector of time differences for each shooting. Its length is written `M`. If `M == 1`, then the simple shooting is implemented and the multiple one otherwise. Default: 0
  * `flow::BifurcationKit.AbstractFlow`: `flow::Flow`: implements the flow of the Cauchy problem though the structure [`Flow`](@ref). Default: Flow()
  * `ds::Any`: Default: diff(LinRange(0, 1, M + 1))
  * `section::Any`: `section`: implements a phase condition. The evaluation `section(x, T)` must return a scalar number where `x` is a guess for **one point** on the periodic orbit and `T` is the period of the guess. Also, the method `section(x, T, dx, dT)` must be available and which returns the differential of `section`. The type of `x` depends on what is passed to the newton solver. See [`SectionSS`](@ref) for a type of section defined as a hyperplane. Default: nothing
  * `parallel::Bool`: `parallel` whether the shooting is computed in parallel (threading). Available through the use of Flows defined by `EnsembleProblem` (this is automatically set up for you). Default: false
  * `par::Any`: `par` parameters of the model Default: nothing
  * `lens::Any`: `lens` parameter axis. Default: nothing
  * `update_section_every_step::UInt64`: updates the section every `update_section_every_step` step during continuation Default: 1
  * `jacobian::BifurcationKit.AbstractJacobianType`: Describes the type of jacobian used in Newton iterations (see below). Default: AutoDiffDense()

## Jacobian

  * `jacobian` Specify the choice of the linear algorithm, which must belong to `[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]`. This is used to select a way of inverting the jacobian dG

      * For `MatrixFree()`, matrix free jacobian, the jacobian is specified by the user in `prob`. This is to be used with an iterative solver (e.g. GMRES) to solve the linear system
      * For `AutoDiffMF()`, we use Automatic Differentiation (AD) to compute the (matrix-free) derivative of `x -> prob(x, p)` using a directional derivative. This is to be used with an iterative solver (e.g. GMRES) to solve the linear system
      * For `AutodiffDense()`. Same as for `AutoDiffMF` but the jacobian is formed as a dense Matrix. You can use a direct solver or an iterative one.
      * For `FiniteDifferences()`, same as for `AutoDiffDense` but we use Finite Differences to compute the jacobian of `x -> prob(x, p)` using the `δ = 1e-8` which can be passed as an argument.
      * For `AutoDiffDenseAnalytical()`. Same as for `AutoDiffDense` but the jacobian is formed using a mix of AD and analytical formula.
      * For `FiniteDifferencesMF()`, use Finite Differences to compute the matrix-free jacobian of `x -> prob(x, p)` using the `δ = 1e-8` which can be passed as an argument.

## Simplified constructors

  * The first important constructor is the following which is used for branching to periodic orbits from Hopf bifurcation points:

```
pb = ShootingProblem(M::Int, prob::Union{ODEProblem, EnsembleProblem}, alg; kwargs...)
```

  * A convenient way to build the functional is to use:

```
pb = ShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, centers::AbstractVector; kwargs...)
```

where `prob` is an `ODEProblem` (resp. `EnsembleProblem`) which is used to create a flow using the ODE solver `alg` (for example `Tsit5()`). `centers` is list of `M` points close to the periodic orbit, they will be used to build a constraint for the phase. `parallel = false` is an option to use Parallel simulations (Threading) to simulate the multiple trajectories in the case of multiple shooting. This is efficient when the trajectories are relatively long to compute. Finally, the arguments `kwargs` are passed to the ODE solver defining the flow. Look at `DifferentialEquations.jl` for more information. Note that, in this case, the derivative of the flow is computed internally using Finite Differences.

  * Another way to create a Shooting problem with more options is the following where in particular, one can provide its own scalar constraint `section(x)::Number` for the phase:

```
pb = ShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, M::Int, section; parallel = false, kwargs...)
```

or

```
pb = ShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, ds, section; parallel = false, kwargs...)
```

  * The next way is an elaboration of the previous one

```
pb = ShootingProblem(prob1::Union{ODEProblem, EnsembleProblem}, alg1, prob2::Union{ODEProblem, EnsembleProblem}, alg2, M::Int, section; parallel = false, kwargs...)
```

or

```
pb = ShootingProblem(prob1::Union{ODEProblem, EnsembleProblem}, alg1, prob2::Union{ODEProblem, EnsembleProblem}, alg2, ds, section; parallel = false, kwargs...)
```

where we supply now two `ODEProblem`s. The first one `prob1`, is used to define the flow associated to `F` while the second one is a problem associated to the derivative of the flow. Hence, `prob2` must implement the following vector field $\tilde F(x,y,p) = (F(x,p), dF(x,p)\cdot y)$.
