```
steadystate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0), Δt::Float64 = 0.01, input::Union{Nothing,Function} = nothing) -> Array{Float64,1}
```

The `steadystate` function is used to evaluate the steady state of the model object that has been built using the `build` function.

### Arguments

  * `model::BSTModel`: A model object that has been built using the `build` function.
  * `tspan::Tuple{Float64,Float64}`: A tuple that defines the time span for the simulation. The default is `(0.0,20.0)`.
  * `Δt::Float64`: The time step for the simulation. The default is `0.01`.
  * `input::Union{Nothing,Function}`: An optional input function that can be used to drive the simulation. The default is `nothing`.

### Returns

  * A vector of state values that represent the steady state of the system.
