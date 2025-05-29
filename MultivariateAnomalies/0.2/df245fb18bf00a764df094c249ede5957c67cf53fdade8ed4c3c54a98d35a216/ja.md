```
sMSC(datacube, cycle_length)
```

与えられた年の長さ `cycle_length` に基づいて、データキューブから中央値の季節サイクルを引きます。

# 例

```
julia> dc = hcat(rand(193) + 2* sin.(0:pi/24:8*pi), rand(193) + 2* sin.(0:pi/24:8*pi))
julia> sMSC_dc = sMSC(dc, 48)
```
