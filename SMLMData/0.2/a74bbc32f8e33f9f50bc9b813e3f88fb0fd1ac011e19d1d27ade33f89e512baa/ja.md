```
理想カメラ(pixel_centers_x::AbstractUnitRange, pixel_centers_y::AbstractUnitRange, pixel_size::T) where T<:Real
```

ピクセル中心位置とスカラーのピクセルサイズを指定して、正方形のピクセルを持つ理想カメラを構築します。

# 引数

  * `pixel_centers_x::AbstractUnitRange`: x方向のピクセル中心インデックスの範囲（通常は1:N）
  * `pixel_centers_y::AbstractUnitRange`: y方向のピクセル中心インデックスの範囲（通常は1:M）
  * `pixel_size::Real`: ピクセルのサイズ（マイクロメートル単位）

# 戻り値

IdealCamera{T} ただし T は pixel_size の型に一致します

# 型パラメータ

  * `T`: すべての空間測定のための数値型（例：Float64、Float32）

# 例

```julia
# 0.1マイクロメートルの正方形ピクセルを持つ512x512カメラを作成
cam = IdealCamera(1:512, 1:512, 0.1)

# Float32精度で作成
cam32 = IdealCamera(1:512, 1:512, 0.1f0)
```

注意: ピクセル (1,1) は物理座標で (pixel*size/2, pixel*size/2) に中心があります。
