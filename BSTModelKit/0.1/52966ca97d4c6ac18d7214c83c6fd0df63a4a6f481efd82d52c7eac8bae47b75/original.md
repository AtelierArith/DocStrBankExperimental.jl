```
evaluate(model::BSTModel; tspan::Tuple{Float64,Float64} = (0.0,20.0), Δt::Float64 = 0.01, 
    input::Union{Nothing,Function} = nothing) -> Tuple{Array{Float64,1}, Array{Float64,2}}
```

This function is used to evaluate the model object that has been built using the `build` function.  The `evaluate` function will return a tuple with two elements: a vector of time points and a matrix of state values.

### Arguments

  * `model::BSTModel`: A model object that has been built using the `build` function.
  * `tspan::Tuple{Float64,Float64}`: A tuple that defines the time span for the simulation. The default is `(0.0,20.0)`.
  * `Δt::Float64`: The time step for the simulation. The default is `0.01`.
  * `input::Union{Nothing,Function}`: An optional input function that can be used to drive the simulation. The default is `nothing`.

### Returns

  * A tuple with two elements:

      * `Array{Float64,1}`: A vector of time points.
      * `Array{Float64,2}`: A matrix of state values.
