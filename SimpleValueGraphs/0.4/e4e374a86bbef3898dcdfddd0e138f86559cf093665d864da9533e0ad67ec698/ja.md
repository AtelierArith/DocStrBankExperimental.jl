```
add_edge!(g::AbstractValGraph, s, d, [values])
add_edge!(g::AbstractValGraph, s, d; val=value)
```

グラフ `g` にエッジ `e = (s, d, values)` を追加し、エッジの値を設定します。

`g` にエッジの値がない場合、`values` は省略できます。

単一のエッジ値を持つグラフの場合、その値は `val` キーワード引数を使って指定することもできます。

エッジが正常に追加された場合は `true` を返し、そうでない場合は `false` を返します。エッジがすでに存在する場合は `false` を返しますが、エッジの値は変更されます。
