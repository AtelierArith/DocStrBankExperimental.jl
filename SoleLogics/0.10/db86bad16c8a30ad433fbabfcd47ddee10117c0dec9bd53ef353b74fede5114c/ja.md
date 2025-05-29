```
struct TruthDict{D<:AbstractDict{A where A<:Atom,T where T<:Truth}} <: AbstractAssignment
    truth::D
end
```

有限集合の原子に真理値を明示的に割り当てる辞書としてインスタンス化された論理的解釈。

# 例

```julia-repl
julia> TruthDict(1:4)
TruthDict with values:
┌────────┬────────┬────────┬────────┐
│      4 │      2 │      3 │      1 │
│  Int64 │  Int64 │  Int64 │  Int64 │
├────────┼────────┼────────┼────────┤
│      ⊤ │      ⊤ │      ⊤ │      ⊤ │
└────────┴────────┴────────┴────────┘


julia> t1 = TruthDict(1:4, false); t1[5] = true; t1
TruthDict with values:
┌───────┬───────┬───────┬───────┬───────┐
│     5 │     4 │     2 │     3 │     1 │
│ Int64 │ Int64 │ Int64 │ Int64 │ Int64 │
├───────┼───────┼───────┼───────┼───────┤
│     ⊤ │     ⊥ │     ⊥ │     ⊥ │     ⊥ │
└───────┴───────┴───────┴───────┴───────┘

julia> t2 = TruthDict(["a" => true, "b" => false, "c" => true])
TruthDict with values:
┌────────┬────────┬────────┐
│      c │      b │      a │
│ String │ String │ String │
├────────┼────────┼────────┤
│      ⊤ │      ⊥ │      ⊤ │
└────────┴────────┴────────┘

julia> check(parseformula("a ∨ b"), t2)
true

```

!!! note
    不明な原子の値を要求された場合、エラーが発生します。ブール値、整数値、または浮動小数点値が指定された場合、それらは`Truth`値に変換されます。構造が空で初期化されると、[`BooleanTruth`](@ref)値が仮定されます。


他に[`AbstractAssignment`](@ref)、[`AbstractInterpretation`](@ref)、[`DefaultedTruthDict`](@ref)、[`BooleanTruth`](@ref)を参照してください。
