```
pointgroup(ops:AbstractVector{SymOperation{D}})
pointgroup(sg::AbstractGroup)
```

空間群 `sg` に関連付けられた点群を計算します（演算子のセット `ops` によって特徴付けられ、格子の平行移動と共同で空間群を生成します）。これは、平行移動部分を「取り除き」、その後、結果として得られるユニークな回転操作に還元することによって得られます。（技術的には、Bradley & Cracknell の言語では、これは `sg` のいわゆる同型点群と呼ばれます；セクション 1.5 を参照してください）。

`SymOperation` の `Vector` を返します。
