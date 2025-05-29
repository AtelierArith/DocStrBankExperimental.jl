```julia
struct IntensityCamera{T, A} <: Krang.AbstractCamera
```

観測者が放射状の無限大に座っているときの高速光線追跡情報をキャッシュするカメラ。この観測者のフレームはボイヤー・リンドクイストフレームと整列しています。
