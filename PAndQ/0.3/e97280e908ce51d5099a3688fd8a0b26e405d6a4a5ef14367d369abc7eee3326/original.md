```
not_or(p, q)
p ↓ q
```

Logical [non-disjunction](https://en.wikipedia.org/wiki/Logical_NOR) operator.

`↓` can be typed by `\downarrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ↓ q)
┌───┬───┬───────┐
│ p │ q │ p ↓ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊥     │
│ ⊥ │ ⊤ │ ⊥     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊥     │
│ ⊥ │ ⊥ │ ⊤     │
└───┴───┴───────┘
```
