```
rcond = oprcondest(op, opinv; exact = false)
```

Compute `rcond`, an estimation of the `1`-norm reciprocal condition number of a linear operator `op`, where `opinv` is the inverse operator `inv(op)`. The estimate is computed as $\text{rcond} = 1 / (\|op\|_1\|opinv\|_1)$, using estimates of the `1`-norm, if `exact = false`, or computed exact values of the `1`-norm, if `exact = true`. The `exact = true` option is not recommended for large order operators.

*Note:* No check is performed to verify that `opinv = inv(op)`.

# Examples

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
