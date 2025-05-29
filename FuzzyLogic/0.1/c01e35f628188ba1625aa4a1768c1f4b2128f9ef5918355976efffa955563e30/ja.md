```julia
struct LinearMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

線形メンバーシップ関数。$a < b$ の場合、増加（S字型）し、それ以外の場合は減少（Z字型）します。

### フィールド

  * `a::Real`: フット。
  * `b::Real`: ショルダー。

### 例

```julia
mf = LinearMF(2, 8)
```
