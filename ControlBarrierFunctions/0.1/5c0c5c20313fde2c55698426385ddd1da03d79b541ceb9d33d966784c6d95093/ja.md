```
SmoothSafetyFilter <: SafetyFilter
```

滑らかなコントローラーで、CBF-QPを任意の精度で近似します。

# フィールド

  * `formula::String` : スムーズセーフティフィルターで使用される式を示す文字列
  * `σ::Float64` : スムージングパラメータ
  * `k::Function` : 安全な制御アクションを計算する関数
