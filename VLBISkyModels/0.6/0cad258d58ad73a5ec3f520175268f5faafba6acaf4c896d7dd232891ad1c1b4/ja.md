```julia
struct RaisedCosinePulse{T} <: VLBISkyModels.Pulse
```

```
RaisedCosinePulse()
RaisedCosinePulse(rolloff)
```

ライズドコサインパルス関数。これは非常にフラットな応答を持つ傾向があり、ロールオフが減衰の速度を制御します。デフォルトでは `rolloff = 0.5` に設定しています。
