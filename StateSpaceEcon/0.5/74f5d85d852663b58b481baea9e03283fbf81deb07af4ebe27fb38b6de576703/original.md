```
simulate(model, plan, data; <options>)
```

Run a simulation for the given model, simulation plan and exogenous data.

### Arguments

```
* `model` - the [`Model`](@ref ModelBaseEcon.Model) instance to simulate.
* `plan` - the [`Plan`](@ref) for the simulation.
* `data` - a 2D `Array` containing the exogenous data. This includes the
    initial and final conditions.
```

### Options as keyword arguments

```
* `fctype::`[`FinalCondition`](@ref) - set the desired final condition type
    for the simulation. The default value is [`fcgiven`](@ref). Other possible
    values include [`fclevel`](@ref), [`fcslope`](@ref) and
    [`fcnatural`](@ref).
* `initial_guess::AbstractMatrix{Float64}` - a 2D `Array` containing the
    initial guess for the solution. This is used to start the Newton-Raphson
    algorithm. The default value is an empty array (`zeros(0,0)`), in which case
    we use the exogenous data for the initial condition. You can use the steady
    state solution using [`steadystatearray`](@ref).
* `deviation::Bool` - set to `true` if the `data` is given in deviations from
    the steady state. In this case the simulation result is also returned as a
    deviation from the steady state. Default value is `false`.
* `anticipate::Bool` - set to `false` to instruct the solver that all shocks
    are unanticipated by the agents. Default value is `true`.
* `solver::Symbol` - specify the simulation solver. Available options are
  :stackedtime and :firstorder. If not given, default is :stackedtime.
* `verbose::Bool` - control whether or not to print progress information.
    Default value is taken from `model.options`.
* `tol::Float64` - set the desired accuracy. Default value is taken from
    `model.options`.
* `maxiter::Int` - algorithm fails if the desired accuracy is not reached
    within this maximum number of iterations. Default value is taken from
    `model.options`.
```

The following options are specific to the `:stackedtime` solver     * `sim_solver` - specify the non-linear solver to use. Available options are        - `:sim_nr` : (default) Newton-Raphson, with possible damping, see below.       - `:sim_lm` : Levenberg–Marquardt       - `:sim_gn` : Gauss-Newton     * `linesearch::Bool` - When `true` the Newton-Raphson is modified to include       a search along the descent direction for a sufficient decrease in f. It       will do this at each iteration. Default is `false`. (Superseded by the       `damping` option described below)     * `damping` - Specifies the style of damping that can be applied to the       Newton non-linear solver. Available options are:       - if not given the default behaviour is no damping, i.e. the damping         coefficient is set to 1.0 in each iteration.       - number: the damping coefficient will be set to the given number (rather than 1)       - vector of numbers: the damping coefficient in each iteration will be set         the number in the corresponding entry of the given vector. If there are         more Newton iterations than the length of the vector, the last entry         will be used until in the remaining iterations.       - `:linesearch` or `:armijo` : same as setting `linesearch=true`. The         Armijo rule is taken from "C.T.Kelly, Iterative Methods for Linear and         Nonlinear Equations, ch.8.1, p.137"       - `(:armijo, :sigma => 0.5, :alpha => 1e-4)` - override the default         parameters of the Armijo rule.       - `:br81` : (experimental) implements the damping algorithm in "Bank, R.E.,         Rose, D.J. Global approximate Newton methods. Numer. Math. 37, 279–295         (1981)."       - `(:br81, :rateK => 10, :delta => 0.1)` : override the default parameters         of the Bank & Rose (1981) algorithm.
