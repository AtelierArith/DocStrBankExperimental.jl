```
print_table(::IO = stdout, xs...; kwargs...)
```

Print a [`TruthTable`](@ref).

The parameters can be a `TruthTable`, iterable of propositions, or sequence of propositions.

Keyword parameters are passed to [`PrettyTables.pretty_table`](https://ronisbr.github.io/PrettyTables.jl/stable/lib/library/#PrettyTables.pretty_table-Tuple{Any}).

# Examples

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
