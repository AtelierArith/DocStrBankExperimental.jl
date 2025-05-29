```
subformulas(f::Formula; sorted=true)
```

与えられた式のすべての部分式を返します（`sorted=true` の場合はサイズでソートされます）。

# 例

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

他にも [`SyntaxTree`](@ref))、[`Formula`](@ref) を参照してください。
