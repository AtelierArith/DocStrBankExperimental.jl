```
imply(p, q)
p → q
```

Logical [implication](https://en.wikipedia.org/wiki/Material_conditional) operator.

`→` can be typed by `\rightarrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p → q)
┌───┬───┬───────┐
│ p │ q │ p → q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊤     │
│ ⊥ │ ⊤ │ ⊤     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊥     │
│ ⊥ │ ⊥ │ ⊤     │
└───┴───┴───────┘
```
