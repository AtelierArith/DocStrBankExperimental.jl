```
BoundedQuadratic(lb::Real, ub::Real, p::Real, q::Real, r::Real)
```

有界二次関数を表します

$$
f(x) = px^2 + qx + r, ∀ x ∈ [lb, ub]
$$

フィールドは次のことを表します：

  * `lb`: 関数の下限
  * `ub`: 関数の上限
  * `p`: 二次項の係数
  * `q`: 一次項の係数
  * `r`: 定数

# 例

```jldoctest
julia> bq = BoundedQuadratic(0., 5., 3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [0.00000, 5.00000]

```
