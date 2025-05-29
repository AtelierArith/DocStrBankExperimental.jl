```
OPSMetrics{T<:AbstractFloat}
```

OPsアルゴリズムのメトリクスを格納するための構造体。このオブジェクトは[`opsmetrics`](@ref)関数によって返されます。

# フィールド

  * `Sn::Vector{T}`: 投資期間中の累積資産。
  * `MER::T`: 投資の平均超過リターン（MER）。
  * `IR::T`: 投資期間中のポートフォリオの情報比率（IR）。
  * `APY::T`: 投資の年率収益率（APY）。
  * `Ann_Std::T`: 投資の年率標準偏差（σₚ）。
  * `Ann_Sharpe::T`: 投資の年率シャープ比（SR）。
  * `MDD::T`: 投資の最大ドローダウン（MDD）。
  * `Calmar::T`: 投資のカルマ比率。
  * `AT::T`: 投資の平均回転率（AT）。
