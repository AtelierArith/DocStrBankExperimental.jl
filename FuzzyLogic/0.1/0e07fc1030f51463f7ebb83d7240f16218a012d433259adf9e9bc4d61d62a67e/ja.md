```julia
struct SShapeMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

S字型メンバーシップ関数。

### フィールド

  * `a::Real`: 足部。
  * `b::Real`: 肩部。

### 例

```julia
mf = SShapeMF(1, 8)
```
