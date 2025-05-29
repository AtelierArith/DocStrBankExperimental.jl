```julia
initialize!(model, clock)

```

Initializes `model` by launching component task for each of the component of `model`. The pairs component and component tasks are recordedin the task manager of the `model`. The `model` clock is [`set!`](@ref) and the files of [`Writer`](@ref) are openned.
