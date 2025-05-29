```
interpret(
    φ::Formula,
    i::AbstractInterpretation,
    args...;
    kwargs...
)::Formula
```

論理的解釈（またはモデル）に対する式の真理値を返します。

# 例

```julia-repl
julia> @atoms p q
2-element Vector{Atom{String}}:
 p
 q

julia> td = TruthDict([p => true, q => false])
TruthDict with values:
┌────────┬────────┐
│      q │      p │
│ String │ String │
├────────┼────────┤
│      ⊥ │      ⊤ │
└────────┴────────┘

julia> interpret(CONJUNCTION(p,q), td)
⊥
```

他にも [`check`](@ref), [`Formula`](@ref), [`AbstractInterpretation`](@ref), [`AbstractAlgebra`](@ref) を参照してください。
