```julia
eachmatrix(
    L::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray
) -> Any

```

LowerTriangularArraysの非水平方向の次元に対するイテレータ。次のように使用します。

```
for k in eachmatrix(L)
    L[1, k]
```

Lのすべての非水平方向の次元をループするために。
