```
QPSafetyFilter <: SafetyFilter
```

制御バリア関数に基づく二次計画問題 (CBF-QP) を解決するコントローラーです。

対応するQPを解くためにOSQPを使用します。

# フィールド

  * `k::Function` : 安全な制御アクションを計算する関数
