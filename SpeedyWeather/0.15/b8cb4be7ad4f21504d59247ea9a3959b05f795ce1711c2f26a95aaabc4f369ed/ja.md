```julia
add!(
    D::Dict{Symbol, SpeedyWeather.AbstractCallback},
    callbacks::SpeedyWeather.AbstractCallback...;
    verbose
)

```

キーを指定せずに、ランダムに作成された callback_???? のようなキーを持つ Dict{Symbol, AbstractCallback} 辞書に1つまたは複数のコールバックを追加します。使用例は次の通りです。

```
add!(model.callbacks, callback)
add!(model.callbacks, callback1, callback2).
```
