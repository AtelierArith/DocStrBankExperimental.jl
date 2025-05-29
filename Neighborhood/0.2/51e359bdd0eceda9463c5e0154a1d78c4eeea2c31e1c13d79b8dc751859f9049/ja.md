```
searchstructure(S, data, metric; kwargs...) → ss
```

与えられた `data` と `metric` に基づいて、タイプ `S`（例：`KDTree, BKTree, VPTree` など）の検索構造 `ss` を作成します。データ型とサポートされているメトリック型はパッケージ固有ですが、一般的な選択肢は Distances.jl の `<:Metric` のサブタイプです。一般的なメトリックのいくつかは Neighborhood.jl によって再エクスポートされています。
