```julia
struct SemiEllipticMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

半楕円形メンバーシップ関数。

### フィールド

  * `cd::Real`: 中心。
  * `rd::Real`: 半軸。

### 例

```julia
mf = SemiEllipticMF(5.0, 4.0)
```
