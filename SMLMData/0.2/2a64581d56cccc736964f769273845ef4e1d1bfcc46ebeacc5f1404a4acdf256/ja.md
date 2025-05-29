```
理想カメラ(pixel_centers_x::AbstractUnitRange, pixel_centers_y::AbstractUnitRange, 
            pixel_size::Tuple{T, T}) where T<:Real
```

ピクセル中心位置とx,yピクセルサイズを指定して、矩形ピクセルを持つ理想カメラを構築します。

# 引数

  * `pixel_centers_x::AbstractUnitRange`: x方向のピクセル中心インデックスの範囲（通常は1:N）
  * `pixel_centers_y::AbstractUnitRange`: y方向のピクセル中心インデックスの範囲（通常は1:M）
  * `pixel_size::Tuple{T, T}`: マイクロメートル単位の(x*サイズ, y*サイズ)のタプル

# 戻り値

ピクセルサイズの型に一致するIdealCamera{T}

# 型パラメータ

  * `T`: すべての空間測定の数値型（例：Float64、Float32）

# 例

```julia
# 矩形ピクセルを持つ512x256カメラを作成（0.1 x 0.15マイクロメートル）
cam = IdealCamera(1:512, 1:256, (0.1, 0.15))

# Float32精度で作成
cam32 = IdealCamera(1:512, 1:256, (0.1f0, 0.15f0))
```

注意: ピクセル(1,1)は物理座標で(pixel*size[1]/2, pixel*size[2]/2)に中心があります。
