```julia
struct TrapezoidalMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

台形メンバーシップ関数。

### フィールド

  * `a::Real`: 左の足。
  * `b::Real`: 左の肩。
  * `c::Real`: 右の肩。
  * `d::Real`: 右の足。

### 例

```julia
mf = TrapezoidalMF(1, 3, 7, 9)
```
