```
@scalarformula expr
```

Parse a logical formula on scalar conditions, such as `V1 > 10`. Note that logical operators take precedence over comparison operators, so it is often the case that expressions such as `V1 > 10` must be wrapped in parentheses.

# Examples

```julia-repl
julia> φ = @scalarformula ((V1 > 10) ∧ (V2 < 0) ∧ (V2 < 0) ∧ (V2 <= 0)) ∨ ((V1 <= 0) ∧ ((V1 <= 3)) ∧ (V2 >= 2))
SyntaxBranch: (V1 > 10 ∧ V2 < 0 ∧ V2 < 0 ∧ V2 ≤ 0) ∨ (V1 ≤ 0 ∧ V1 ≤ 3 ∧ V2 ≥ 2)
```

See also [`parseformula`](@ref), [`syntaxstring`](@ref).
