```
rays(pm::PropagationModel, tx1::AcousticSource, θ::Real, rmax)
```

`tx1`から角度`θ`で発射された光線を計算します（`θ`がベクトルの場合はすべての角度）。`RayArrival`データ型の配列を返します。`rmax`は光線を追跡する最大水平範囲（メートル単位）です。
