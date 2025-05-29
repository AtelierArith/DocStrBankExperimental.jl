```
swap!(tree::Tree, idx::Integer, old_new::Pair{<:Integer, <:Integer})
```

指定された `idx` ノードの2つの子要素を入れ替えます。 `old_new` の `old` と `new` は `idx` ノードの子でなければなりません。入れ替えに失敗した場合は `ture` を返し、それ以外の場合は `true` を返します。
