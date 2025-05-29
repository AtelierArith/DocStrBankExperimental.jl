```julia
function dispersion(x::UniData, mean::Real)
```

`mean`を中心とした`x`の要素の二乗偏差の合計。

`mean`は提供されなければならず、実数でなければなりません。

*例*

```julia
using PermutationTests
x=randn(10)
d=dispersion(x, μ(x))
```
