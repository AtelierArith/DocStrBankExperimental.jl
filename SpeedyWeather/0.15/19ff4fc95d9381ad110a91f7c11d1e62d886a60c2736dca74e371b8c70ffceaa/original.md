```julia
add!(
    D::Dict{Symbol, SpeedyWeather.AbstractCallback},
    key_callbacks::Pair{Symbol, <:SpeedyWeather.AbstractCallback}...
)

```

Add a or several callbacks to a Dict{String, AbstractCallback} dictionary. To be used like

```
add!(model.callbacks, :my_callback => callback)
add!(model.callbacks, :my_callback1 => callback, :my_callback2 => other_callback)
```
