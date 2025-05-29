```
new_trace = map_optimize(trace, selection::Selection,
    max_step_size=0.1, tau=0.5, min_step_size=1e-16, verbose=false)
```

選択された連続的な選択肢に対してトレースの対数確率を最適化するために、バックトラッキング勾配上昇を実行します。

選択されたランダムな選択肢は、全実数直線上にサポートを持たなければなりません。
