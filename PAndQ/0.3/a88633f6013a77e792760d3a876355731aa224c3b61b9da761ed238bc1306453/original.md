```
not_imply(p, q)
p ↛ q
```

Logical [non-implication](https://en.wikipedia.org/wiki/Material_nonimplication) operator.

`↛` can be typed by `\nrightarrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ↛ q)
┌───┬───┬───────┐
│ p │ q │ p ↛ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊥     │
│ ⊥ │ ⊤ │ ⊥     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊤     │
│ ⊥ │ ⊥ │ ⊥     │
└───┴───┴───────┘
```
