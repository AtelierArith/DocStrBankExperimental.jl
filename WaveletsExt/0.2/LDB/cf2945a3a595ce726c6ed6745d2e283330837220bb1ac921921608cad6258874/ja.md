```
discriminant_power(D, tree, dp)
discriminant_power(coefs, y, dp)
```

各葉からの局所判別基底 (LDB) ツリーの判別力を返します。

# 引数

  * `D::AbstractArray{T} where T<:AbstractFloat`: 判別測定値。
  * `tree::BitVector`: 最大の判別測定値を持つ係数を選択するための最良基底ツリー。
  * `coefs::AbstractArray{T} where T<:AbstractFloat`: 入力信号のための最良基底係数。
  * `y::AbstractVector{S} where S`: `coefs` の各信号に対応するラベル。
  * `dp::DiscriminantPower`: 判別力の測定値。

!!! note
    `discriminant_power(D, tree, dp)` は `dp = BasisDiscriminantMeasure()` のみで機能し、`discriminant_power(coefs, y, dp)` は `dp = FishersClassSeparability()` および `dp = RobustFishersClassSeparability()` に対して機能します。


# 返り値

  * `power::Array{T}`: `D` または `coefs` の各インデックスでの判別力。
  * `order::Vector{T}`: 降順の判別力の順序。
