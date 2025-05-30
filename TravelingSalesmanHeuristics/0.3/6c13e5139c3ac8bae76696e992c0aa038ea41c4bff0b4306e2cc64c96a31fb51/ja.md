```
repetitive_heuristic(distmat::Matrix, heuristic::Function, repetitive_kw::Symbol; keywords...)
```

各 `i` に対して `1:n` の範囲で、キーワード `repetitive_kw` を `i` に設定して `heuristic` を実行します。タプル `(bestpath, bestcost)` を返します。デフォルトでは、`repetitive_kw` は `:firstcity` であり、これは `farthest_insertion`、`cheapest_insertion`、および `nearest_neighbor` ヒューリスティックに適しています。

`repetitive_heuristic` に渡された任意のキーワードは、`heuristic` の各呼び出しに渡されます。例えば、`repetitive_heuristic(dm, nearest_neighbor; do2opt = true)` は、`n` 個の最近傍経路それぞれに対して 2-opt を実行します。

!!! note
    繰り返しヒューリスティック呼び出しはスレッドで並列化されています。最適な速度を得るために、Julia が複数のスレッドで実行されていることを確認してください。

