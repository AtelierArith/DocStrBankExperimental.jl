```
compute_control(mpc,x;r,uprev)
```

与えられたMPC `mpc`と状態`x`に対して、最適な制御アクションを計算します。オプションの引数：

  * `r` - 参照値
  * `uprev` - 前の制御アクション

すべての引数はデフォルトでゼロです。
