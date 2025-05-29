```julia
struct DualAverage{T<:AbstractFloat}
```

DualAverageの調整情報と実行時パラメータを含みます。

# フィールド

  * `adaption::BaytesMCMC.DualAverageParameter`
  * `μ::AbstractFloat`: 目標受け入れ率のための上方バイアス - 提案は0から離れるように上方にバイアスされています。
  * `t::Int64`: 時間更新、0から始まります
  * `H̄::AbstractFloat`: Hoffman(2014)の最初の方程式の平均部分、p 1607, (6)
  * `logϵ::AbstractFloat`: ログステップ
  * `logϵ̄::AbstractFloat`: 平均化されたログステップ
