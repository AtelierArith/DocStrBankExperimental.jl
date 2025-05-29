```
is_isometric(L::AbstractLat, M::AbstractLat; depth::Int = -1, bacher_depth::Int = 0) -> Bool
```

格子 `L` と `M` が同型であるかどうかを返します。

パラメータ `depth` と `bacher_depth` を正の値に設定すると、パフォーマンスが向上する可能性があります。`-1`（デフォルト）に設定された場合、使用される `depth` の値は `L` の階数に応じてヒューリスティックに選択されます。デフォルトでは、`bacher_depth` は `0` に設定されています。
