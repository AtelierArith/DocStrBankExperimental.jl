```
ErrorPropagator([::Type{T}; N_args, capacity::Int])
```

`capacity`の各`N_args`入力に対して（少なくとも）`capacity`個の値を処理できる`ErrorPropagator`を作成します。

デフォルトは`T = Float64`、`N_args = 2`、および`capacity = 2^32-1 ≈ 4e9`です。
