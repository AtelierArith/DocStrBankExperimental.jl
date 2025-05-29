```julia
function dispersion(x::UniData; 
    centered::Bool=false, mean::Realo=nothing)
```

もし `centered` が true の場合、`x` の要素の二乗の合計を返します。

そうでなければ、

もし `mean` が提供されている場合、`x` の要素が `mean` からの二乗偏差の合計を返します。

そうでなければ、

`x` の要素がその平均からの二乗偏差の合計を返します。

*例*

```julia
using PermutationTests
x=randn(10)
x0=μ0(x)
μx=μ(x)
m=μ(x)

# 効率の降順
d1=dispersion(x0)
d2=dispersion(x, mean=μx)
d3=dispersion(x)
d1==d2==d3 # -> true
```
