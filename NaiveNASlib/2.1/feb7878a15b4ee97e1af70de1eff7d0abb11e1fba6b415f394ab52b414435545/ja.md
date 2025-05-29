```
remove!(v::MutationVertex, strategy=RemoveStrategy())
```

`v`をグラフから削除するには、`inputs`(@ref)と`outputs`(@ref)から削除します。

`v`の入力と出力をどのように再接続するか、また`v`の`inputs`と`outputs`の入力サイズと出力サイズをどのように整列させるかの戦略を提供することが可能です。

デフォルトの戦略は、まず`v`の`nin==nout`を設定し、その後、すべての`inputs`(@ref)をすべての`outputs`(@ref)に接続することです。
