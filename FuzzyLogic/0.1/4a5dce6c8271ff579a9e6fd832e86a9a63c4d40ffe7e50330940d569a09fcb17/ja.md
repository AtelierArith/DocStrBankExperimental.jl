```julia
struct PiShapeMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Π型メンバーシップ関数。

### フィールド

  * `a::Real`: 左の足。
  * `b::Real`: 左の肩。
  * `c::Real`: 右の肩。
  * `d::Real`: 右の足。

### 例

```julia
mf = PiShapeMF(1, 4, 5, 10)
```
