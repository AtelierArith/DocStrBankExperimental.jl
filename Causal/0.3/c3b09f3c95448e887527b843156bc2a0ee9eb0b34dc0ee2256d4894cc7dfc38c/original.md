```julia
run!(model, clock)
run!(model, clock, withbar)

```

Runs the `model` by triggering the components of the `model`. This triggering is done by generating clock tick using the model clock `model.clock`. Triggering starts with initial time of model clock, goes on with a step size of the sampling period of the model clock, and finishes at the finishing time of the model clock. If `withbar` is `true`, a progress bar indicating the simulation status is displayed on the console.

!!! warning
    The `model` must first be initialized to be run. See also: [`initialize!`](@ref).

