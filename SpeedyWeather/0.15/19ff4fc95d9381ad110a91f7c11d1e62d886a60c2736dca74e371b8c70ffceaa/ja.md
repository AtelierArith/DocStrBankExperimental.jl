```julia
add!(
    D::Dict{Symbol, SpeedyWeather.AbstractCallback},
    key_callbacks::Pair{Symbol, <:SpeedyWeather.AbstractCallback}...
)

```

Dict{String, AbstractCallback} 辞書に1つまたは複数のコールバックを追加します。次のように使用します。

```
add!(model.callbacks, :my_callback => callback)
add!(model.callbacks, :my_callback1 => callback, :my_callback2 => other_callback)
```
