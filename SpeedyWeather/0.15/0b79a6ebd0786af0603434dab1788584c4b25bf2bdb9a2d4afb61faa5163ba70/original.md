```julia
add!(
    model::SpeedyWeather.AbstractModel,
    key_callbacks::Pair{Symbol, <:SpeedyWeather.AbstractCallback}...
) -> Any

```

Add a or several callbacks to a model::AbstractModel. To be used like

```
add!(model, :my_callback => callback)
add!(model, :my_callback1 => callback, :my_callback2 => other_callback)
```
