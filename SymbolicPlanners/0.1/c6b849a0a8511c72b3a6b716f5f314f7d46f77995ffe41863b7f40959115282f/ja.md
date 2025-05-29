```
PruningHeuristic(heuristic::Heuristic, pruner)
```

既存の `heuristic` を `pruner` と組み合わせます。`pruner` は、[`filter_available`](@ref) および [`filter_relevant`](@ref) 関数を定義するアクションプルーニングメソッドです。たとえば、`pruner` はアクションをフィルタリングする別のヒューリスティックである可能性があります。
