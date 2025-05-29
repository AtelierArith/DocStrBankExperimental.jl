```
subformulas(f::Formula; sorted=true)
```

Return all sub-formulas (sorted by size when `sorted=true`) of a given formula.

# Examples

```julia-repl
julia> syntaxstring.(SoleLogics.subformulas(parseformula("◊((p∧q)→r)")))
6-element Vector{String}:
 "p"
 "q"
 "r"
 "p ∧ q"
 "◊(p ∧ q)"
 "(◊(p ∧ q)) → r"
```

See also [`SyntaxTree`](@ref)), [`Formula`](@ref).
