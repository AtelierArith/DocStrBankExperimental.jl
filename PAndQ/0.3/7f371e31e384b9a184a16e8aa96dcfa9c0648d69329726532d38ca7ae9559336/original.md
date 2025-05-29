```
not_converse_imply(p, q)
p ↚ q
```

Logical [converse non-implication](https://en.wikipedia.org/wiki/Converse_nonimplication) operator.

`↚` can be typed by `\nleftarrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ↚ q)
┌───┬───┬───────┐
│ p │ q │ p ↚ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊥     │
│ ⊥ │ ⊤ │ ⊤     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊥     │
│ ⊥ │ ⊥ │ ⊥     │
└───┴───┴───────┘
```
