```
get_MedianCycles(datacube, cycle_length::Int = 46)
```

は、年次サイクルの長さ（プリセット: `cycle_length = 46`）が与えられたときに、データキューブの中央値年次サイクルを返します。データキューブは2次元、3次元、または4次元であり、時間は最初の次元に格納されています。

# 例

```
julia> using MultivariateAnomalies
julia> dc = hcat(rand(193) + 2* sin(0:pi/24:8*pi), rand(193) + 2* sin(0:pi/24:8*pi))
julia> cycles = get_MedianCycles(dc, 48)
```
