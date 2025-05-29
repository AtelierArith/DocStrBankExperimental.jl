```
bdplot_boundarymap(bmap, intervals; figkwargs = NamedTuple(), kwargs...)
```

[`DynamicalBilliards.boundarymap`](@ref) の出力を、障害物の弧長に関する情報を正しく表示する軸にプロットします。`figure, axis` を返します。

境界マップの並列化バージョンにも対応しています。

## キーワード引数

  * `figkwargs = NamedTuple()` は `Figure` に伝播されるキーワードです。
  * `color` : プロットされた点に使用する色です。単一の色または `length(bmap)` の長さの色のベクトルのいずれかで、各初期条件に異なる色を与えることができます（並列化バージョン用）。
  * その他のすべてのキーワードは `scatter!` に伝播されます。
