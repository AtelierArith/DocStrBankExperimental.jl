```
struct DefaultedTruthDict{
    D<:AbstractDict{A where A<:Atom,T where T<:Truth},
    T<:Truth
} <: AbstractAssignment
    truth::D
    default_truth::T
end
```

辞書としてインスタンス化された真理値表とデフォルト値。この構造体は、一連の原子に真理値を割り当て、辞書に存在しない原子の値を要求された場合には `default_truth` を返します。

# 実装

[`interpret`](@ref) 関数を使用し、[`AbstractAssignment`](@ref) として [`DefaultedTruthDict`](@ref) を渡し、[`Atom`](@ref) が辞書に存在しない場合、デフォルトの辞書値が返され、[`Atom`](@ref) 自体は返されません。

以下はその例です。

```julia-repl
julia> interpret(Atom(5), DefaultedTruthDict(string.(1:4), false))
⊥
```

# 例

```julia-repl
julia> t1 = DefaultedTruthDict(string.(1:4), false); t1["5"] = false; t1
DefaultedTruthDict with default truth `⊥` and values:
┌────────┬────────┬────────┬────────┬────────┐
│      4 │      1 │      5 │      2 │      3 │
│ String │ String │ String │ String │ String │
├────────┼────────┼────────┼────────┼────────┤
│      ⊤ │      ⊤ │      ⊥ │      ⊤ │      ⊤ │
└────────┴────────┴────────┴────────┴────────┘

julia> check(parseformula("1 ∨ 2"), t1)
true

julia> check(parseformula("1 ∧ 5"), t1)
false

```

[`AbstractAssignment`](@ref)、[`AbstractInterpretation`](@ref)、[`interpret`](@ref)、[`Atom`](@ref)、[`TruthDict`](@ref)、[`DefaultedTruthDict`](@ref) も参照してください。
