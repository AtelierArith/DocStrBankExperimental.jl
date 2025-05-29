```julia
add!(
    model::SpeedyWeather.AbstractModel,
    callbacks::SpeedyWeather.AbstractCallback...
)

```

モデルにキーを指定せずにコールバックを1つまたは複数追加します。キーはランダムに生成されます（例: callback_????）。使用方法は次の通りです。

```
add!(model.callbacks, callback)
add!(model.callbacks, callback1, callback2).
```
