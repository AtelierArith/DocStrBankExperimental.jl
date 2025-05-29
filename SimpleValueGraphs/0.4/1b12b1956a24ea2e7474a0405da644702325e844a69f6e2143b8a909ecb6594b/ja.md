```
add_vertex!(g::AbstractValGraph[, values])
add_vertex!(g::AbstractValGraph; val=value)
```

グラフ `g` に頂点を追加し、頂点の値を設定します。

`g` に頂点の値がない場合、`values` は省略できます。

単一の頂点値を持つグラフの場合、その値は `val` キーワード引数を使って指定することもできます。

頂点が正常に追加された場合は `true` を返し、そうでない場合は `false` を返します。
