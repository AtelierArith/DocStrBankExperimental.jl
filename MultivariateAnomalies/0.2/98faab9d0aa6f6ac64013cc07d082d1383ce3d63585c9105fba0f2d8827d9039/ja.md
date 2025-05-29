```
get_MedianCycle!(init_MC, dat::Array{tp,1})
```

`get_MedianCycle()`のメモリ効率の良いバージョンで、`init_MC[3]`に中央値のサイクルを返します。`init_MC`オブジェクトは`init_MedianCycle`で作成する必要があります。いくつかのNaN値に対処できます。

# 例

```
julia> using MultivariateAnomalies
julia> dat = rand(193) + 2* sin(0:pi/24:8*pi)
julia> dat[100] = NaN
julia> init_MC = init_MedianCycle(dat, 48)
julia> get_MedianCycle!(init_MC, dat)
julia> init_MC[3]
```
