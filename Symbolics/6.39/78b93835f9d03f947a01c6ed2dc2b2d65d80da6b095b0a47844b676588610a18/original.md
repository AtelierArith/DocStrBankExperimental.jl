```julia
symbolic_linear_solve(eq, var; simplify, check) -> Any

```

Solve equation(s) `eqs` for a set of variables `vars`.

Assumes `length(eqs) == length(vars)`

Currently only works if all equations are linear. `check` if the expr is linear w.r.t `vars`.

# Examples

```jldoctest
julia> @variables x y
2-element Vector{Num}:
 x
 y

julia> Symbolics.symbolic_linear_solve(x + y ~ 0, x)
-y

julia> Symbolics.symbolic_linear_solve([x + y ~ 0, x - y ~ 2], [x, y])
2-element Vector{Float64}:
  1.0
 -1.0
```
