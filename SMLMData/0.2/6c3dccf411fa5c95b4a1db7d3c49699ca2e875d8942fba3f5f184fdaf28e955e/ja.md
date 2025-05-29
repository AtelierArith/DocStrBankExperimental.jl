```
IdealCamera(n_pixels_x::Integer, n_pixels_y::Integer, pixel_size::T) where T<:Real
```

平方ピクセルを持つIdealCameraを、ピクセル数とピクセルサイズから直接構築します。

# 引数

  * `n_pixels_x::Integer`: x次元のピクセル数
  * `n_pixels_y::Integer`: y次元のピクセル数
  * `pixel_size::Real`: ピクセルのサイズ（マイクロメートル単位）

# 戻り値

IdealCamera{T} ただし T は pixel_size の型に一致します

# 例

```julia
# 0.1マイクロメートルの平方ピクセルを持つ512x512カメラを作成
cam = IdealCamera(512, 512, 0.1)

# Float32精度で作成
cam32 = IdealCamera(512, 512, 0.1f0)
```
