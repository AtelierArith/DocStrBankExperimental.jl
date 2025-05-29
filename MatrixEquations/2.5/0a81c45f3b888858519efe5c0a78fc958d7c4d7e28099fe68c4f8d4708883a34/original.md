```
γ = opnorm1est(op)
```

Compute `γ`, a lower bound of the `1`-norm of the square linear operator `op`, using reverse communication based computations to evaluate `op * x` and `op' * x`. It is expected that in most cases $\gamma > \|op\|_1/10$, which is usually acceptable for estimating the condition numbers of linear operators.

# Examples

```jldoctest
julia> A = [-6. -2. 1.; 5. 1. -1; -4. -2. -1.]
3×3 Array{Float64,2}:
 -6.0  -2.0   1.0
  5.0   1.0  -1.0
 -4.0  -2.0  -1.0

julia> opnorm1est(lyapop(A))
18.0

julia> opnorm1est(invlyapop(A))
3.76666666666667
```
