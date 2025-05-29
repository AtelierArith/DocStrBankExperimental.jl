```
TunableQPSafetyFilter <: SafetyFilter
```

制御バリア関数に基づく二次計画問題 (CBF-QP) を調整可能なクラス K 関数で解決するコントローラー。

対応する QP を解くために OSQP を使用します。

# フィールド

  * `k::Function` : 安全な制御アクションを計算する関数
