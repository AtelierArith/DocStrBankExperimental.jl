```
offset(::AbstractSkyCoords, separation, pa) -> coordinate
```

与えられた角度の分離 `separation`（ラジアン）と位置角 `pa`（ラジアン）によって座標をオフセットします。

球面座標における正弦法則と余弦法則を使用し、対極に対する補正を行います。入力と同じタイプの天球座標を返します。

# 例

```jldoctest
julia> c1 = ICRSCoords(0, 0);

julia> c2 = offset(c1, deg2rad(1), deg2rad(90))
ICRSCoords{Float64}(0.017453292519943295, 1.0686516840418957e-18)

julia> offset(c1, c2) .|> rad2deg
(1.0, 90.0)
```

# 参照

  * [`separation`](@ref), [`position_angle`](@ref)
