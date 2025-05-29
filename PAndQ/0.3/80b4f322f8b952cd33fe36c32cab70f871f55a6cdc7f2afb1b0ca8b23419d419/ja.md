```
solutions(p)
```

`interpret(valuation, p) == ⊤` となる [`valuations`](@ref) の状態を持つイテレータを返します。

真の解釈をもたらすすべての評価を見つけるには、命題を [`normalize`](@ref) を使用して論理積標準形に変換します。そうでない場合、[`tseytin`](@ref) 変換を使用して、それらの評価のサブセットが特定されます。

[`interpret`](@ref) と [`tautology`](@ref) も参照してください。

# 例

```jldoctest
julia> map(collect, solutions(⊤))
1-element Vector{Vector{Any}}:
 []

julia> @atomize map(collect, solutions(p))
1-element Vector{Vector{Pair{PAndQ.Variable, Bool}}}:
 [PAndQ.Variable(:p) => 1]

julia> map(collect, solutions(⊥))
Any[]
```
