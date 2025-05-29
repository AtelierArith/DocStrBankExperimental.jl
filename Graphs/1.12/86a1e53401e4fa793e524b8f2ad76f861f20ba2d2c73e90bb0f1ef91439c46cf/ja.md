```
abstract type IncrementalCycleTracker
```

増分サイクル検出問題のためのスーパタイプ。抽象型コンストラクタ `IncrementalCycleTracker(G)` は、特定の増分サイクル検出アルゴリズムを自動的に選択するために使用される場合があります。使用例については [`add_edge_checked!`](@ref) を参照してください。
