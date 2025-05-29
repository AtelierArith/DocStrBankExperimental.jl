```
or(p, q)
p ∨ q
```

Logical [disjunction](https://en.wikipedia.org/wiki/Logical_disjunction) operator.

`∨` can be typed by `\vee[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(p ∨ q)
┌───┬───┬───────┐
│ p │ q │ p ∨ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊤     │
│ ⊥ │ ⊤ │ ⊤     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊤     │
│ ⊥ │ ⊥ │ ⊥     │
└───┴───┴───────┘
```
