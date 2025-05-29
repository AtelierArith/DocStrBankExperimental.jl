```
dijkstra(N::T, source::K) where {T <: DeterministicNetwork, K}
```

ソース種からの最短/最も簡単な経路を返すダイクストラのアルゴリズム。出力形式については、`bellman_ford`のグローバルドキュメントを参照してください。
