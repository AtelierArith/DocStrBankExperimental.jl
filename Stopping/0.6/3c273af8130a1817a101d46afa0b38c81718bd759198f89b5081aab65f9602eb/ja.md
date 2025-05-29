```
`update_and_start!(stp::AbstractStopping; no_opt_check::Bool = false, kwargs...)`
```

状態の値を更新し、停止を初期化します。問題の最適性ステータスをブール値として返します。

注意:

  * Kwargsは`update!`呼び出しに転送されます。
  * `no_opt_check`は`start!`での最適性チェックをスキップします（デフォルトは`false`）。
