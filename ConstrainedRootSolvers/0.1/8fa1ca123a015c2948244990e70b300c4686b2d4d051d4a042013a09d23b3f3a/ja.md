1Dルートソルバーのためのリデュースステップ法。この方法は、改善が見られなくなるまで初期推定値から増加または減少します。その後、増分ステップが減少し、ルートソルバーは続行します。

```julia
mutable struct ReduceStepMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# フィールド

  * `x_min::AbstractFloat`: 下限
  * `x_max::AbstractFloat`: 上限
  * `x_ini::AbstractFloat`: 初期推定値
  * `Δ_ini::AbstractFloat`: 初期ステップ
  * `history::Vector`: すべてのシミュレーションの履歴
