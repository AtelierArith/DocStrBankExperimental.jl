```
RectangularAperture(x, y, w, h, θ=0)
RectangularAperture(position, w, h, θ=0)
```

長方形のアパーチャ。

幅 `w`、高さ `h`、および位置角 `θ`（度単位）のある長方形のアパーチャ。

# 例

```jldoctest
julia> ap = RectangularAperture(0, 0, 10, 4, 0)
11×5 RectangularAperture{Int64} with indices -5:5×-2:2:
 0.25  0.5  0.5  0.5  0.25
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.5   1    1    1    0.5
 0.25  0.5  0.5  0.5  0.25
```
