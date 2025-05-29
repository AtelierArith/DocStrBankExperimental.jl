```
tsirelson_bound(CG::Array, scenario::Tuple, level; verbose::Bool = false, dualize::Bool = false, solver = Hypatia.Optimizer{_solver_type(T)})
```

マルチパーティのベル機能 `CG` のツィレルソン境界を上限します。これはコリンズ-ギシン表記で書かれています。`scenario` は入力と出力の数を詳細に示すタプルで、順序は (oa, ob, ..., ia, ib, ...) です。`level` は整数または "1 + A B" のような文字列で、NPA階層のレベルを決定します。`verbose` はソルバーの出力が印刷されるかどうかを決定します。`dualize` は代数問題が代わりに解かれるかどうかを決定します。警告: これはパフォーマンスにとって重要であり、正しい選択はソルバーに依存します。
