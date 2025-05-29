```
not_and(p, q)
p ↑ q
```

Logical [non-conjunction](https://en.wikipedia.org/wiki/Sheffer_stroke) operator.

`↑` can be typed by `\uparrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ↑ q)
┌───┬───┬───────┐
│ p │ q │ p ↑ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊥     │
│ ⊥ │ ⊤ │ ⊤     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊤     │
│ ⊥ │ ⊥ │ ⊤     │
└───┴───┴───────┘
```
