```
readvariable(meta::MetaVLSV, var::String, ids::Vector{Int}) -> Array
```

`meta` に関連付けられたセルのコレクション `ids` から変数 `var` を読み取ります。`ids` が空の場合、`var` の全体をソートされた配列として返します。
