```
movingls(::Type{T}, grid::VoronoiGrid, p::VoronoiPolygon, fun; h,  kernel)
```

与えられた関数のテイラー展開を移動最小二乗法を使用して見つけます。最初の引数 `T` は次のいずれかである必要があります：

  * LinearExpansion
  * QuadraticExpansion
  * CubicExpansion

ポリゴン `p` は関数 `fun` のテイラー展開が計算される場所です。キーワード引数 `h` は移動半径です。これは十分に大きくする必要があります。そうでないと、テイラー展開が未定義になる可能性があります。カーネルは（重み付き）最小二乗問題を定義するために使用される重み付け関数です。
