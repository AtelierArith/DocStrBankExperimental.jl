```julia
add!(
    model::SpeedyWeather.AbstractModel,
    key_callbacks::Pair{Symbol, <:SpeedyWeather.AbstractCallback}...
) -> Any

```

モデル::AbstractModelに1つまたは複数のコールバックを追加します。次のように使用します。

```
add!(model, :my_callback => callback)
add!(model, :my_callback1 => callback, :my_callback2 => other_callback)
```
