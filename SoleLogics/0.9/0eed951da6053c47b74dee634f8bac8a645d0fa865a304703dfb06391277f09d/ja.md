```
check(
    φ::Formula,
    i::AbstractInterpretation,
    args...;
    kwargs...
)::Bool
```

論理的解釈（またはモデル）に対して式をチェックし、式の真理値が `istop` であれば `true` を返します。このプロセスは（有限）[モデル検査](https://en.wikipedia.org/wiki/Model_checking)と呼ばれ、通常は論理の複雑さに依存する多くのアルゴリズムがあります。

# 例

```julia-repl
julia> @atoms String p q
2-element Vector{Atom{String}}:
 Atom{String}("p")
 Atom{String}("q")

julia> td = TruthDict([p => TOP, q => BOT])
TruthDict with values:
┌────────┬────────┐
│      q │      p │
│ String │ String │
├────────┼────────┤
│      ⊥ │      ⊤ │
└────────┴────────┘

julia> check(CONJUNCTION(p,q), td)
false
```

他にも [`interpret`](@ref), [`Formula`](@ref), [`AbstractInterpretation`](@ref), [`TruthDict`](@ref) を参照してください。
