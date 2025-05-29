```
IntensityMap(data::AbstractArray, fovx::Real, fovy::Real, x0::Real=0, y0::Real=0; header=NoHeader())
```

ピクセルフラックス `data` と視野 (`fovx`, `fovy`) および中心ピクセルオフセット (`x0`, `y0`) を持つ空間グリッドを使用して IntensityMap を作成し、ヘッダー `header` を指定します。
