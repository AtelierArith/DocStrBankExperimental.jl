```
automorphism_group_order(L::AbstractLat; depth::Int = -1, bacher_depth::Int = 0) -> Int
```

与えられた定義格子 `L` に対して、`L` の自己同型群の順序を返します。

パラメータ `depth` と `bacher_depth` を正の値に設定すると、パフォーマンスが向上する可能性があります。`-1`（デフォルト）に設定された場合、使用される `depth` の値は `L` の階数に応じてヒューリスティックに選択されます。デフォルトでは、`bacher_depth` は `0` に設定されています。
