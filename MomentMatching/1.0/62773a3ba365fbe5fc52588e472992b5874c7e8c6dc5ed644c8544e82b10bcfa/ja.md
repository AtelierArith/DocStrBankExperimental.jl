```julia
struct BootstrapResult{S<:Real}
```

# 説明

ブートストラップ結果を格納するための構造体。

# フィールド

  * `moms`: シミュレートされたモーメント
  * `xs`: シミュレートされたパラメータ値
  * `sd_asymp`: 漸近標準誤差
  * `W`: 効率的重み行列
