```
print_table(::IO = stdout, xs...; kwargs...)
```

[`TruthTable`](@ref)を印刷します。

パラメータは`TruthTable`、命題の反復可能なコレクション、または命題のシーケンスであることができます。

キーワードパラメータは[`PrettyTables.pretty_table`](https://ronisbr.github.io/PrettyTables.jl/stable/lib/library/#PrettyTables.pretty_table-Tuple{Any})に渡されます。

# 例

```jldoctest
julia> print_table(TruthTable([⊤]))
┌───┐
│ ⊤ │
├───┤
│ ⊤ │
└───┘

julia> @atomize print_table([p])
┌───┐
│ p │
├───┤
│ ⊤ │
│ ⊥ │
└───┘

julia> @atomize print_table(p ∧ q)
┌───┬───┬───────┐
│ p │ q │ p ∧ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊤     │
│ ⊥ │ ⊤ │ ⊥     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊥     │
│ ⊥ │ ⊥ │ ⊥     │
└───┴───┴───────┘
```
