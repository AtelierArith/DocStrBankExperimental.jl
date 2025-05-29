```
γ = opnorm1(op)
```

Compute `γ`, the induced `1`-norm of the linear operator `op`, as the maximum of `1`-norm of the columns of the associated `m x n` matrix $M$ `= Matrix(op)`:

$$
\gamma = \|op\|_1 := \max_{1 ≤ j ≤ n} \|M_j\|_1
$$

with $M_j$ the `j`-th column of $M$. This function is not recommended to be used for large order operators.

# Examples

```jldoctest
julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> opnorm1(lyapop(A))
30.0

julia> opnorm1(invlyapop(A))
3.7666666666666706
```
