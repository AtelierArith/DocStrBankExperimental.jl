1D根解法の二分法

```julia
mutable struct BisectionMethod{FT<:AbstractFloat} <: ConstrainedRootSolvers.AbstractCRSMethod{FT<:AbstractFloat}
```

# フィールド

  * `x_min::AbstractFloat`: 下限
  * `x_max::AbstractFloat`: 上限
  * `xy::Matrix{FT} where FT<:AbstractFloat`: xとyを格納する行列で、find_peakで使用される
  * `history::Vector`: すべてのシミュレーションの履歴
