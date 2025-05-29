```
err=eval_runerr(
    graph,
    x;
    vals = nothing,
    relerrs = nothing,
    input = :A,
    output = size(graph.outputs, 1),
    mode = :bounds, # Can be :bounds, :rand, :estimate
    add_relerr = eps(),
)
```

`x`で評価されたグラフの実行エラーを提供します。`vals`と`output`の意味については[`eval_graph`](@ref)を参照してください。キーワード引数`relerrs`は各ノードの実行エラー推定のための類似の変数です。キーワード引数`mode`は`：bounds`、`：rand`、`：estimate`のいずれかで、コードが推定または境界を作成するか、境界内のランダムエラーを指定します。
