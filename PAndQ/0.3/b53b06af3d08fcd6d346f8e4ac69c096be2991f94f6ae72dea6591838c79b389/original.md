```
exclusive_or(p, q)
p ↮ q
```

Logical [exclusive disjunction](https://en.wikipedia.org/wiki/Exclusive_or) operator.

`↮` can be typed by `\nleftrightarrow[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ↮ q)
┌───┬───┬───────┐
│ p │ q │ p ↮ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊥     │
│ ⊥ │ ⊤ │ ⊤     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊤     │
│ ⊥ │ ⊥ │ ⊥     │
└───┴───┴───────┘
```
