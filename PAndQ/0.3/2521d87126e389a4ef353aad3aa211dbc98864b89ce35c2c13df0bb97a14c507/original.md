```
TruthTable(ps)
```

Construct a [truth table](https://en.wikipedia.org/wiki/Truth_table) for the given propositions.

The header is a sequence of propositions. The body is a matrix where the rows are [`interpretations`](@ref) of each proposition in the header.

Propositions logically equivalent to a [truth value](@ref nullary_operators) will be grouped on the left, followed by those equivalent to an atomic proposition, and then by all other propositions. Logically equivalent propositions will be grouped together. Propositions that have the same text representation will only be shown once.

# Examples

```jldoctest
julia> TruthTable([⊤])
┌───┐
│ ⊤ │
├───┤
│ ⊤ │
└───┘

julia> @atomize TruthTable([¬p])
┌───┬────┐
│ p │ ¬p │
├───┼────┤
│ ⊤ │ ⊥  │
│ ⊥ │ ⊤  │
└───┴────┘

julia> @atomize TruthTable([p ∧ ¬p, p → q, ¬p ∨ q])
┌────────┬───┬───┬───────────────┐
│ p ∧ ¬p │ p │ q │ p → q, ¬p ∨ q │
├────────┼───┼───┼───────────────┤
│ ⊥      │ ⊤ │ ⊤ │ ⊤             │
│ ⊥      │ ⊥ │ ⊤ │ ⊤             │
├────────┼───┼───┼───────────────┤
│ ⊥      │ ⊤ │ ⊥ │ ⊥             │
│ ⊥      │ ⊥ │ ⊥ │ ⊤             │
└────────┴───┴───┴───────────────┘
```
