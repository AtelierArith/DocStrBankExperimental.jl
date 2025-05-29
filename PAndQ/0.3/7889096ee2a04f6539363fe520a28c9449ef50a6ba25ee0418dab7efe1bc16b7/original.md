```
not_exclusive_or(p, q)
p ↔ q
```

Logical [exclusive non-disjunction](https://en.wikipedia.org/wiki/Logical_biconditional) operator.

`↔` can be typed by `\leftrightarrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ↔ q)
┌───┬───┬───────┐
│ p │ q │ p ↔ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊤     │
│ ⊥ │ ⊤ │ ⊥     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊥     │
│ ⊥ │ ⊥ │ ⊤     │
└───┴───┴───────┘
```
