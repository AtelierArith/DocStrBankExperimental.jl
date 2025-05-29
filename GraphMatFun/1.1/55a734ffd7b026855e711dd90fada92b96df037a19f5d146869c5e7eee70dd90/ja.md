```
compress_graph_redundant!(
    graph,
    cref = [];
    compress_lincomb = true,
    verbose = false,
)
```

グラフから冗長なノードを削除します。つまり、グラフ内ですでに存在する計算を繰り返すノードです。線形結合に対応するノードは、係数が同じであり、`compress_lincomb`が`true`に設定されている場合にのみ削除されます。
