```
add_edge!(g, u, v, s, val)
add_edge!(g, u, v, d)

MetaGraph `g` にエッジ `(u, v)` を追加し、オプションのプロパティ `s` に値 `val` を持たせるか、シンボルを値にマッピングするオプションの辞書 `d` で与えられたプロパティを追加します。

エッジが追加された場合は true を返し、そうでない場合は false を返します。
```
