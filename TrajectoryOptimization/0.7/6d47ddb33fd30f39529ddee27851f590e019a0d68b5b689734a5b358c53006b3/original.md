```
Problem{T}
```

Trajectory Optimization Problem. Contains the full definition of a trajectory optimization problem, including:

  * dynamics model (`RD.DiscreteDynamics`)
  * objective ([`Objective`](@ref))
  * constraints ([`ConstraintList`](@ref))
  * initial and final states
  * Primal variables (state and control trajectories)
  * Discretization information: knot points (`N`), time step (`dt`), and total time (`tf`)

# Constructors:

```julia
Problem(model, obj, constraints, x0, xf, Z, N, tf)
Problem(model, obj, x0, tf; [xf, constraints, N, X0, U0, dt, integration])
```

where `Z` is a [`RobotDynamics.SampledTrajectory`].

# Arguments

  * `model`: A `DiscreteDynamics` model. If a `ContinuousDynamics` model is provided, it will          be converted to a `DiscretizedDynamics` model via the integrator specified by the          `integration` keyword argument.
  * `obj`: Objective
  * `X0`: Initial state trajectory. If omitted it will be initialized with NaNs, to be later overwritten by the solver.
  * `U0`: Initial control trajectory. If omitted it will be initialized with zeros.
  * `x0`: Initial state
  * `xf`: Final state. Defaults to zeros.
  * `dt`: Time step. Can be either a vector of length `N-1` or a positive real number.
  * `tf`: Final time. Set to zero.
  * `N`: Number of knot points. Uses the length of the objective.
  * `integration`: One of the defined integration types to discretize the continuous dynamics model.

Both `X0` and `U0` can be either a `Matrix` or a `Vector{<:AbstractVector}`.
