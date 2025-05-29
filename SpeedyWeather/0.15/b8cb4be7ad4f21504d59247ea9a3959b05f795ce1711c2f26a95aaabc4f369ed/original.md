```julia
add!(
    D::Dict{Symbol, SpeedyWeather.AbstractCallback},
    callbacks::SpeedyWeather.AbstractCallback...;
    verbose
)

```

Add a or several callbacks to a Dict{Symbol, AbstractCallback} dictionary without specifying the key which is randomly created like callback_????. To be used like

```
add!(model.callbacks, callback)
add!(model.callbacks, callback1, callback2).
```
