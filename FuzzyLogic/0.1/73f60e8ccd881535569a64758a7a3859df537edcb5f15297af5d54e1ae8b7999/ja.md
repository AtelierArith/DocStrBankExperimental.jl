```julia
struct PiecewiseLinearMF{T<:Real, S<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

区間線形メンバーシップ関数。

### フィールド

  * `points::Array{Tuple{T, S}, 1} where {T<:Real, S<:Real}`

### 注意事項

入力が2つの点の間にある場合、そのメンバーシップ度は線形補間によって計算されます。入力が最初の点の前にある場合、最初の点と同じメンバーシップ度を持ちます。入力が最後の点の後にある場合、最初の点と同じメンバーシップ度を持ちます。

### 例

```julia
mf = PiecewiseLinearMF([(1, 0), (2, 1), (3, 0), (4, 0.5), (5, 0), (6, 1)])
```
