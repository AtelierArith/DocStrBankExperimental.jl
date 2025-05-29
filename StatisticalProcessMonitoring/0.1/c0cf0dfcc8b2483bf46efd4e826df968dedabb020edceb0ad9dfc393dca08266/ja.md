```
OneSidedEWMA(λ, value, upw::Bool)
```

OneSidedEWMA統計量は、設計パラメータ`λ`と初期値`value`を持ちます。

新しい観測値`x`に基づく更新メカニズムは次のように与えられます：

  * `upw == true`の場合、$C_t = \max\{0, (1-λ)\cdot C_{t-1} + λ\cdot x\}$;
  * `upw == false`の場合、$C_t = \min\{0, (1-λ)\cdot C_{t-1} + λ\cdot x\}$;

### 引数

  * `λ::Float64`: スムージング定数。デフォルトは`0.1`です。
  * `value::Float64`: 統計量の現在の値。デフォルトは`0.0`です。
  * `upw::Bool`: 統計量がプロセスの平均の増加（`true`）または減少（`false`）を監視するべきかどうか。デフォルトは`true`です。
