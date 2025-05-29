```
set_solver(OPT_NAME::Module = HiGHS, verb::Bool = false)
```

は使用する最適化ソルバーを設定します。

これにより、自動的に `clear_solver_options()` が呼び出され、次に（オプションの）`verb` 引数の値に基づいて詳細出力のための適切なオプションが設定されます。
