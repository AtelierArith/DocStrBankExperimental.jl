ニュートン法は1次元の根の解法において最小および最大範囲によって制約されています

```julia
mutable struct NewtonBisectionMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# フィールド

  * `x_min::AbstractFloat`: 下限
  * `x_max::AbstractFloat`: 上限
  * `x_ini::AbstractFloat`: 初期推定
  * `history::Vector`: すべてのシミュレーションの履歴
