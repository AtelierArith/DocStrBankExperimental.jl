```
make_compute_exp_tendency(model::AbstractModel)
```

`compute_exp_tendency!` 関数を返し、明示的にステップされる状態変数を更新します。このフォールバックは、このモデルのすべての傾向をゼロに設定します。これは、更新する明示的な傾向を持たないモデルに適しています。統合された LSM の場合、すべてのモデルの傾向を上書きしてしまうため、ここで `dY .= 0` を設定することはできません。

`compute_exp_tendency!` は SciMLBase.jl ソルバーと互換性があるべきです。
