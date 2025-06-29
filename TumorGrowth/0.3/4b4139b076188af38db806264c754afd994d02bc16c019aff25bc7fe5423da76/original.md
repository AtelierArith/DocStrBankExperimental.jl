```
    CalibrationProblem(times, volumes, model; learning_rate=0.0001, options...)
```

Specify a problem concerned with optimizing the parameters of a tumor growth `model`, given measured `volumes` and corresponding `times`.

See [`TumorGrowth`](@ref) for a list of possible `model`s.

Default optimisation is by Adam gradient descent, using a sum of squares loss. Call `solve!` on a problem to carry out optimisation, as shown in the example below. See "Extended Help" for advanced options, including early stopping.

Initial values of the parameters are inferred by default.

Unless frozen (see "Extended help" below), the calibration process learns an initial condition `v0` which is generally different from `volumes[1]`.

# Simple solve

```julia
using TumorGrowth

times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
volumes = [0.00023, 8.4e-5, 6.1e-5, 4.3e-5, 4.3e-5, 4.3e-5]
problem = CalibrationProblem(times, volumes, gompertz; learning_rate=0.01)
solve!(problem, 30)    # apply 30 gradient descent updates
julia> loss(problem)   # sum of squares loss
1.7341026729860452e-9

p = solution(problem)
julia> pretty(p)
"v0=0.0002261  v∞=2.792e-5  ω=0.05731"


extended_times = vcat(times, [42.0, 46.0])
julia> gompertz(extended_times, p)[[7, 8]]
2-element Vector{Float64}:
 3.374100207406809e-5
 3.245628908921241e-5
```

# Extended help

# Solving with iteration controls

Continuing the example above, we may replace the number of iterations, `n`, in `solve!(problem, n)`, with any control from IterationControl.jl:

```julia
using IterationControl
solve!(
  problem,
  Step(1),            # apply controls every 1 iteration...
  WithLossDo(),       # print loss
  Callback(problem -> print(pretty(solution(problem)))), # print parameters
  InvalidValue(),     # stop for ±Inf/NaN loss
  NumberSinceBest(5), # stop when lowest loss so far was 5 steps prior
  TimeLimit(1/60),    # stop after one minute
  NumberLimit(400),   # stop after 400 steps
)
p = solution(problem)
julia> loss(problem)
7.609310030658547e-10
```

See [IterationControl.jl](https://github.com/JuliaAI/IterationControl.jl) for all options.

!!! note
    Controlled iteration as above is not recommended if you specify `optimiser=LevenbergMarquardt()` or `optimiser=Dogleg()` because the internal state of these optimisers is reset at every `Step`. Instead, to arrange automatic stopping, use `solve!(problem, 0)`.


# Visualizing results

```julia
using Plots
scatter(times, volumes, xlab="time", ylab="volume", label="train")
plot!(problem, label="prediction")
```

# Keyword options

  * `p0=guess_parameters(times, volumes, model)`: initial value of the model parameters.
  * `lower`: named tuple indicating lower bounds on components of the model parameter `p`. For example, if `lower=(; v0=0.1)`, then this introduces the constraint `p.v0 < 0.1`. The model-specific default value is [`TumorGrowth.lower_default(model)`](@ref).
  * `upper`: named tuple indicating upper bounds on components of the model parameter `p`. For example, if `upper=(; v0=100)`, then this introduces the constraint `p.v0 < 100`. The model-specific default value is [`TumorGrowth.upper_default(model)`](@ref).
  * `frozen`: a named tuple, such as `(; v0=nothing, λ=1/2)`; indicating parameters to be frozen at specified values during optimisation; a `nothing` value means freeze at initial value. The model-specific default value is [`TumorGrowth.frozen_default(model)`](@ref).
  * `learning_rate > 0`: learniing rate for Adam gradient descent optimisation. Ignored if `optimiser` is explicitly specified.
  * `optimiser`: optimisation algorithm, which will be one of two varieties:

      * A gradient descent optimiser: This must be from Optimisers.jl or implement the same API.
      * A Gauss-Newton optimiser: Either `LevenbergMarquardt()`, `Dogleg()`, provided by LeastSquaresOptim.jl (but re-exported by `TumorGrowth`).

    The model-specific default value is [`TumorGrowth.optimiser_default(model)`](@ref), unless `learning_rate` is specified, in which case it will be `Optimisers.Adam(learning_rate)`.
  * `scale`: a scaling function with the property that `p = scale(q)` has a value of the same order of magnitude for the model parameters being optimised, whenever `q` has the same form as a model parameter `p` but with all values equal to one. Scaling can help components of `p` converge at a similar rate. Ignored by Gauss-Newton optimisers. Model-specific default is [`TumorGrowth.scale_default(model)`](@ref).
  * `radius > 0`: initial trust region radius. This is ignored unless `optimiser` is a Gauss-Newton optimiser. The model-specific default is [`TumorGrowth.radius_default(model, optmiser)`](@ref), which is typically `10.0` for `LevenbergMarquardt()` and `1.0` for `Dogleg`.
  * `half_life=Inf`: set to a real positive number to replace the sum of squares loss with a weighted version; weights decay in reverse time with the specified `half_life`. Ignored by Gauss-Newton optimisers.
  * `penalty ≥ 0`: the larger the positive value, the more a loss penalty discourages large differences in `v0` and `v∞` on a log scale. Helps discourage `v0` and `v∞` drifting out of bounds in models whose ODE have a singularity at the origin. Model must include `v0` and `v∞` as parameters. Ignored by Gauss-Newton optimisers.  The model-specific default value is [`TumorGrowth.penalty_default(model)`](@ref).
  * `ode_options...`: optional keyword arguments for the ODE solver, `DifferentialEquations.solve`, from DifferentialEquations.jl. Not relevant for models using analytic solutions (see the table at [`TumorGrowth`](@ref)).
