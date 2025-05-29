```
get_EECC(G::SimpleGraph, m₀::Int64)
```

グラフ `G` のエッジ非交差エッジクリークカバー (EECC) を、論文で提案されたヒューリスティックに従って、最大 `m₀` の順序のクリークを考慮して計算します。

# 引数

  * `G::SimpleGraph`: LightGraphs.SimpleGraph 型の単純グラフ
  * `m₀::Int64`: 考慮するクリークの最大順序を表す整数

# 戻り値

EECC を含むベクター
