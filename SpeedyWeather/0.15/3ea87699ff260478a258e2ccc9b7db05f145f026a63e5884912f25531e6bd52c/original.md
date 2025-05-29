```julia
add!(
    model::SpeedyWeather.AbstractModel,
    callbacks::SpeedyWeather.AbstractCallback...
)

```

Add a or several callbacks to a mdoel without specifying the key which is randomly created like callback_????. To be used like

```
add!(model.callbacks, callback)
add!(model.callbacks, callback1, callback2).
```
