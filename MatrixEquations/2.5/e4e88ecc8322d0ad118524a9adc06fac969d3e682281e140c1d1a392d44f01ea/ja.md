```
rcond = oprcondest(op, opinv; exact = false)
```

線形演算子 `op` の `1`-ノルム逆条件数の推定値 `rcond` を計算します。ここで、`opinv` は逆演算子 `inv(op)` です。この推定値は、`exact = false` の場合は `1 / (\|op\|_1\|opinv\|_1)` として計算され、`1`-ノルムの推定値を使用します。`exact = true` の場合は、`1`-ノルムの正確な値が計算されます。`exact = true` オプションは、大きな次数の演算子には推奨されません。

*注意:* `opinv = inv(op)` であることを確認するチェックは行われません。

# 例

```jldoctest
julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> oprcondest(lyapop(A),invlyapop(A))
0.014749262536873142

julia> 1/opnorm1est(lyapop(A))/opnorm1est(invlyapop(A))
0.014749262536873142

julia> oprcondest(lyapop(A),invlyapop(A),exact = true)
0.008849557522123885

julia> 1/opnorm1(lyapop(A))/opnorm1(invlyapop(A))
0.008849557522123885
```
