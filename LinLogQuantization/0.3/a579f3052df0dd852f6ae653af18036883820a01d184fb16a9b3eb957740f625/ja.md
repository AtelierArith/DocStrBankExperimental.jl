```
LinQuantArray(TInteger, A; dims, extrema=nothing)
```

配列 `A` の次元 `dims` に沿って各要素を独立に線形量子化します。

# 引数

  * `TInteger`: 量子化された配列の型
  * `A`: 量子化する配列
  * `dims`: 量子化する次元
  * `extrema`: 範囲の最小値と最大値、デフォルトは `nothing`。

# 戻り値

  * 量子化された配列と元の範囲の最小値と最大値を持つ Vector{LinQuantArray}。
