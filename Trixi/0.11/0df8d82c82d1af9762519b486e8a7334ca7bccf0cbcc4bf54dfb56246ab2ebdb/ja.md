```
ode_unstable_check(dt, u, semi, t)
```

OrdinaryDiffEq.jlで使用される不安定性の基本チェックの実装です。`any(isnan, u)`のようなものをチェックする代わりに、この関数は単に`isnan(dt)`をチェックします。これにより、MPI並列化を使用する際に、追加のグローバル通信が不要になり、すべてのランクが同じ結果を返します。

この関数をキーワード引数`unstable_check=ode_unstable_check`として、MPI並列実行のTrixi.jlでエラーに基づくステップサイズ制御を使用する際にOrdinaryDiffEq.jlの`solve`に渡す必要があります。

[ドキュメント](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)の「その他」セクションを参照してください。
