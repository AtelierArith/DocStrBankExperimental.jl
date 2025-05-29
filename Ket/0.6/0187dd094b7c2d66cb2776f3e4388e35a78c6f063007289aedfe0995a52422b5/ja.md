```
tsirelson_bound(FC::Array, level; verbose::Bool = false, dualize::Bool = false, solver = Hypatia.Optimizer{_solver_type(T)})
```

多項体ベル関数 `FC` のツィレルソン境界の上限を、相関表記で記述します。`level` は整数または "1 + A B" のような文字列で、NPA階層のレベルを決定します。`verbose` はソルバーの出力が印刷されるかどうかを決定します。`dualize` は代数問題が代わりに解かれるかどうかを決定します。警告: これはパフォーマンスにとって重要であり、正しい選択はソルバーに依存します。
