```
IdealCamera(n_pixels_x::Integer, n_pixels_y::Integer, pixel_size::Tuple{T, T}) where T<:Real
```

矩形ピクセルを持つIdealCameraを、ピクセル数とx,yピクセルサイズから直接構築します。

# 引数

  * `n_pixels_x::Integer`: x次元のピクセル数
  * `n_pixels_y::Integer`: y次元のピクセル数
  * `pixel_size::Tuple{T, T}`: マイクロメートル単位の(x*サイズ, y*サイズ)のタプル

# 戻り値

IdealCamera{T} ただし、Tはピクセルサイズの型と一致します

# 例

```julia
# 矩形ピクセル(0.1 x 0.15マイクロメートル)を持つ512x256カメラを作成
cam = IdealCamera(512, 256, (0.1, 0.15))

# Float32精度で作成
cam32 = IdealCamera(512, 256, (0.1f0, 0.15f0))
```
