```
solve_factoring(missolver, mres::FactoringResult, x::Int) -> (Int, Int)
```

単位円グリッドグラフ上のマッピングされた重み付きMIS問題を解くことによって因数分解問題を解決します。$a  b = x$ が成り立つ (a, b) を返します。`missolver(graph, weights)` は解として整数のベクトルを返すべきです。
