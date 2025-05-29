```
ParametricTrajectoryOptimizationProblem(
    cost,
    dynamics,
    inequality_constraints,
    state_dim,
    control_dim,
    parameter_dim,
    horizon,
)
```

Constructs a `ParametricTrajectoryOptimizationProblem` from the given problem data:

  * `cost` is callable as `cost(xs, us, params) -> c` to compute objective value for a given sequence of states `xs` and control inputs `us` for a parameter vector `params`.
  * `dynamics` is callable as `dynamics(x, u, t [, params]) -> xp` to generate the next state `xp` from the previous state `x`, control `u`, time `t` and optional parameters `params`.  See `parameterize_dynamics` for toggling the optional parameter vector.
  * `inequality_constraints` is callable as `inequality_constraints(xs, us, params) -> gs` to generate a vector of constraints `gs` from states `xs` and `us` where the layout and types of `xs` and `us` are the same as for the `cost`. Constraints specified in this form will be enforced as `0 <= gs`; i.e., feasible trajectories evalute to non-negative constraints. If your prolbem has no inequality constraints, set `inequality_constraints = (xs, us, params) -> Symbolics.Num[]`.
  * `state_dim::Integer` is the stagewise dimension of the state.
  * `control_dim::Integer` is the stagewise dimension of the control input.
  * `horizon::Integer` is the horizon of the problem
  * `parameterize_dynamics` controls the optional `params` argument handed to dynamics. This flag is disabled by default. When set to `true`, `dynamics` are called as `dynamics(x, u, t, params)`

instead of `dynamics(x, u, t)`. Note that *all* parameters are handed to the dynamics call

# Note

This function uses `Syombolics.jl` to compile all of the functions, gradients, jacobians, and hessians needed to solve a parametric trajectory optimization problem. Therfore, all callables above must be sufficiently generic to accept `Syombolics.Num`-valued arguments.

Since the setup procedure involves code-generation, calls to this contructor are rather expensive and shold be avoided in tight inner loops. By contrast, repeated solver invokations on the same `ParametricTrajectoryOptimizationProblem` for varying parameter values are very fast. Therefore, it is a good idea to choose a parameterization that avoids re-construction.

Furthermore, note that the *entire* parameter vector is handed to `costs`, `dynamics`, and `inequality_constraints`. This allows parameters to be shared between multiple calls. For example, a parameter that controlls the collision avoidance radius may apear both in the cost and constraints. It's the users responsibility to correctly index into the `params` vector to extract the desired parameters for each call.

# Example

Below we construct a parametric optimization problem for a 2D integrator with 2 states, 2 inputs over a hrizon of 10 stages. Additionally, this problem features ±0.1 box constraints on states and inputs.

```@example running_example
horizon = 10
state_dim = 2
control_dim = 2
cost = (xs, us, params) -> sum(sum((x - params).^2) + sum(u.^2) for (x, u) in zip(xs, us))
dynamics = (x, u, t) -> x + u
inequality_constraints = let
    state_constraints = state -> [state .+ 0.1; -state .+ 0.1]
    control_constraints = control -> [control .+ 0.1; -control .+ 0.1]
    (xs, us, params) -> [
        mapreduce(state_constraints, vcat, xs)
        mapreduce(control_constraints, vcat, us)
    ]
end

problem = ParametricTrajectoryOptimizationProblem(
    cost,
    dynamics,
    inequality_constraints,
    state_dim,
    control_dim,
    horizon
)
```
