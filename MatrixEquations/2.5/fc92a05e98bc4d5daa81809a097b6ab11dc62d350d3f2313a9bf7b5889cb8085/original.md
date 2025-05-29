```
sep = opsepest(opinv; exact = false)
```

Compute `sep`, an estimation of the `1`-norm separation of a linear operator `op`, where `opinv` is the inverse operator `inv(op)`. The estimate is computed as $\text{sep}  = 1 / \|opinv\|_1$ , using an estimate of the `1`-norm, if `exact = false`, or the computed exact value of the `1`-norm, if `exact = true`. The `exact = true` option is not recommended for large order operators.

The separation of the operator `op` is defined as

$$
\text{sep} = \displaystyle\min_{X\neq 0} \frac{\|op*X\|}{\|X\|}.
$$

An estimate of the reciprocal condition number of `op` can be computed as $\text{sep}/\|op\|_1$.

# Example

```jldoctest
julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> opsepest(invlyapop(A))
0.26548672566371656

julia> 1/opnorm1est(invlyapop(A))
0.26548672566371656

julia> opsepest(invlyapop(A),exact = true)
0.26548672566371656

julia> 1/opnorm1(invlyapop(A))
0.26548672566371656
```
