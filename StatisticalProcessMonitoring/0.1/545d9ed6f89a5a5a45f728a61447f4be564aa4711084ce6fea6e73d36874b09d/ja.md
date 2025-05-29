```
optimize_grid(CH::ControlChart, rlconstr::Function, settings::OptSettings)
```

制御チャートを最適化し、グリッドサーチを使用して最適なパラメータのセットを見つけます。

### 引数

  * `CH::ControlChart`: 最適化する必要があるパラメータを持つ制御チャートオブジェクト。
  * `rlconstr::Functiom`: 制御チャートのOCパフォーマンスを評価する関数。
  * `settings::OptSettings`: 最適化設定。

### 戻り値

  * par_current (Vector{Float64}): 最適化アルゴリズムによって見つかった最適なパラメータのセット。

### 参考文献

Qiu, P. (2008). Distribution-Free Multivariate Process Control Based on Log-Linear Modeling. IIE Transactions, 40(7), 664-677. https://doi.org/10.1080/07408170701744843
