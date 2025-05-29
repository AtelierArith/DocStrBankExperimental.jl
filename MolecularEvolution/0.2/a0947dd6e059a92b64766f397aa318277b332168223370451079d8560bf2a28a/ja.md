```
metropolis_step(LL::Function, modifier, curr_value)
```

MCMCにおける標準的なメトロポリスステップを実行します。すなわち、候補を対称的に提案し、候補が拒否されるかどうかによってチェーンの次の状態を返します。

# インターフェース

`MySampler <: Any` を実装する必要があります。

  * `proposal(modifier::MySampler, curr_value)`
  * `log_prior(modifier::MySampler, x)`
  * `apply_decision(modifier::MySampler, accept::Bool)`

`LL` はデフォルトで `curr_value` と `proposal` の返り値に対して呼び出されます。ただし、新しい値を提案する前に現在の値を変換し、次に引数 `LL` が期待する形式に一致させるために逆変換を行うことも可能です。

# 拡張インターフェース

## ハスティングス

非対称的な提案を可能にするために、次をオーバーロードする必要があります。

  * `log_proposal(modifier::MySampler, x, conditioned_on)`

これはデフォルトで定数（特に `0.0`）を返します。

## 変換

変換された空間で提案を行うために、次をオーバーロードします。

  * `tr(modifier::MySampler, x)`
  * `invtr(modifier::MySampler, x)`

これはデフォルトで恒等変換です。
