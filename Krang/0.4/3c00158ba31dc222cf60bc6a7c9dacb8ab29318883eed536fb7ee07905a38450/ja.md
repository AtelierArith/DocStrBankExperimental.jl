```julia
struct SlowLightIntensityCamera{T, A} <: Krang.AbstractCamera
```

放射状無限大に座っている観察者のために遅い光線追跡情報をキャッシュするカメラ。この観察者のフレームはボイヤー・リンドクイストフレームと整列しています。
