```julia
struct TriangularMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

三角メンバーシップ関数。

### フィールド

  * `a::Real`: 左足。
  * `b::Real`: ピーク。
  * `c::Real`: 右足。

### 例

```julia
mf = TriangularMF(3, 5, 7)
```
