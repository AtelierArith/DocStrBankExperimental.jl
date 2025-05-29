```
get_MedianCycle(dat::Array{tp,1}, cycle_length::Int = 46)
```

は、年間サイクルの長さ（プリセット: `cycle_length = 46`）を考慮して、1次元データ配列の中央値年間サイクルを返します。いくつかのNaN値に対処できます。

# 例

```
julia> using MultivariateAnomalies
julia> dat = randn(90) + x = sind.(0:8:719)
julia> cycles = get_MedianCycle(dat, 48)
```
