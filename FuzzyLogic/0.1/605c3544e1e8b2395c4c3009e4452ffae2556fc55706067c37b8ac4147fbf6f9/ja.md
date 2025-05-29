```julia
struct ZShapeMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Z字型メンバーシップ関数。

### フィールド

  * `a::Real`: 肩。
  * `b::Real`: 足。

### 例

```julia
mf = ZShapeMF(3, 7)
```
