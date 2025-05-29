ニュートン・ラフソン法による1次元根解法

```julia
mutable struct NewtonRaphsonMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# フィールド

  * `x_ini::AbstractFloat`: 初期推定値
  * `history::Vector`: すべてのシミュレーションの履歴
