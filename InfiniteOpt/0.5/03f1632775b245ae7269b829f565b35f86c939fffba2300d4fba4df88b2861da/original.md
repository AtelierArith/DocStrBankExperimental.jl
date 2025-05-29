```
JuMP.drop_zeros!(nlp::NLPExpr)::NLPExpr
```

Removes the zeros (possibly introduced by deletion) from an nonlinear expression.  Note this only uses a few simple heuristics and will not remove more complex  relationships like `cos(π/2)`. 

**Example**

```julia-repl
julia> expr = x^2.3 * max(0, zero(NLPExpr)) - exp(1/x + 0)
x^2.3 * max(0, 0) - exp(1 / x + 0)

julia> drop_zeros!(expr)
-exp(1 / x)
```
