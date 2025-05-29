```
KnnResult(ksearch::Integer)
```

固定容量（`ksearch`）の優先キューを作成し、knn結果セットを表します。最初はゼロアイテムから始まり、`ksearch`サイズに達するまで[`push_item!`](@ref)呼び出しで成長します。その後は、距離に基づいて最小のアイテムのみが保持されます。
