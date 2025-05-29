```
ISSfSmoothSafetyFilter <: SafetyFilter
```

入力から状態への安全（ISSf）CBF-QPを任意に近似するスムーズコントローラー。

# フィールド

  * `formula::String` : スムーズセーフティフィルターで使用される式を示す文字列
  * `σ::Float64` : スムージングパラメータ
  * `k::Function` : 安全な制御アクションを計算する関数
  * `ε::Float64` : 一致した不確実性に対するIssfロバストネスパラメータ
