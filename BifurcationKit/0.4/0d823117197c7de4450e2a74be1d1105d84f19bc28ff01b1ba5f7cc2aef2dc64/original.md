```julia
struct PoincareShootingProblem{Tf, Tjac<:BifurcationKit.AbstractJacobianType, Tsection<:BifurcationKit.SectionPS, Tpar, Tlens} <: BifurcationKit.AbstractPoincareShootingProblem
```

This composite type implements the Poincaré Shooting method to locate periodic orbits by relying on Poincaré return maps. More details (maths, notations, linear systems) can be found [here](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitShooting/). The arguments are as described below.

# Fields

  * `M::Int64`: `M`: the number of Poincaré sections. If `M == 1`, then the simple shooting is implemented and the multiple one otherwise. Default: 0
  * `flow::Any`: `flow::Flow`: implements the flow of the Cauchy problem though the structure [`Flow`](@ref). Default: Flow()
  * `section::BifurcationKit.SectionPS`: `sections`: function or callable struct which implements a Poincaré section condition. The evaluation `sections(x)` must return a scalar number when `M == 1`. Otherwise, one must implement a function `section(out, x)` which populates `out` with the `M` sections. See [`SectionPS`](@ref) for type of section defined as a hyperplane. Default: SectionPS(M)
  * `δ::Float64`: `δ = 1e-8` used to compute the jacobian of the functional by finite differences. If set to `0`, an analytical expression of the jacobian is used instead. Default: 0.0
  * `parallel::Bool`: `parallel = false` whether the shooting are computed in parallel (threading). Only available through the use of Flows defined by `EnsembleProblem`. Default: false
  * `par::Any`: `par` parameters of the model Default: nothing
  * `lens::Any`: `lens` parameter axis Default: nothing
  * `update_section_every_step::UInt64`: `update_section_every_step` updates the section every `update_section_every_step` step during continuation Default: 1
  * `jacobian::BifurcationKit.AbstractJacobianType`: Describes the type of jacobian used in Newton iterations (see below). Default: AutoDiffDenseAnalytical()

## Jacobian

  * `jacobian` Specify the choice of the linear algorithm, which must belong to `[AutoDiffMF(), MatrixFree(), AutodiffDense(), AutoDiffDenseAnalytical(), FiniteDifferences(), FiniteDifferencesMF()]`. This is used to select a way of inverting the jacobian dG

      * For `MatrixFree()`, matrix free jacobian, the jacobian is specified by the user in `prob`. This is to be used with an iterative solver (e.g. GMRES) to solve the linear system
      * For `AutoDiffMF()`, we use Automatic Differentiation (AD) to compute the (matrix-free) derivative of `x -> prob(x, p)` using a directional derivative. This is to be used with an iterative solver (e.g. GMRES) to solve the linear system
      * For `AutodiffDense()`. Same as for `AutoDiffMF` but the jacobian is formed as a dense Matrix. You can use a direct solver or an iterative one.
      * For `FiniteDifferences()`, same as for `AutoDiffDense` but we use Finite Differences to compute the jacobian of `x -> prob(x, p)` using the `δ = 1e-8` which can be passed as an argument.
      * For `AutoDiffDenseAnalytical()`. Same as for `AutoDiffDense` but the jacobian is formed using a mix of AD and analytical formula.
      * For `FiniteDifferencesMF()`, use Finite Differences to compute the matrix-free jacobian of `x -> prob(x, p)` using the `δ = 1e-8` which can be passed as an argument.

## Simplified constructors

  * The first important constructor is the following which is used for branching to periodic orbits from Hopf bifurcation points   pb = PoincareShootingProblem(M::Int, prob::Union{ODEProblem, EnsembleProblem}, alg; kwargs...)
  * A convenient way is to create a functional is

`pb = PoincareShootingProblem(prob::ODEProblem, alg, section; kwargs...)`

for simple shooting or

`pb = PoincareShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, M::Int, section; kwargs...)`

for multiple shooting . Here `prob` is an `Union{ODEProblem, EnsembleProblem}` which is used to create a flow using the ODE solver `alg` (for example `Tsit5()`). Finally, the arguments `kwargs` are passed to the ODE solver defining the flow. We refer to `DifferentialEquations.jl` for more information.

  * Another convenient call is

`pb = PoincareShootingProblem(prob::Union{ODEProblem, EnsembleProblem}, alg, normals::AbstractVector, centers::AbstractVector; δ = 1e-8, kwargs...)`

where `normals` (resp. `centers`) is a list of normals (resp. centers) which defines a list of hyperplanes $\Sigma_i$. These hyperplanes are used to define partial Poincaré return maps.

## Computing the functionals

A functional, hereby called `G` encodes this shooting problem. You can then call `pb(orbitguess, par)` to apply the functional to a guess. Note that `orbitguess::AbstractVector` must be of size M * N where N is the number of unknowns in the state space and `M` is the number of Poincaré maps. Another accepted `guess` is such that `guess[i]` is the state of the orbit on the `i`th section. This last form allows for non-vector state space which can be convenient for 2d problems for example.

Note that you can generate this guess from a function solution using `generate_solution`.

  * `pb(orbitguess, par)` evaluates the functional G on `orbitguess`
  * `pb(orbitguess, par, du)` evaluates the jacobian `dG(orbitguess).du` functional at `orbitguess` on `du`
  * `pb`(Val(:JacobianMatrixInplace), J, x, par)` compute the jacobian of the functional analytically. This is based on ForwardDiff.jl. Useful mainly for ODEs.
  * `pb(Val(:JacobianMatrix), x, par)` same as above but out-of-place.

!!! tip
    You can use the function `getperiod(pb, sol, par)` to get the period of the solution `sol` for the problem with parameters `par`.

