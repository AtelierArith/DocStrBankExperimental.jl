```
not(p)
¬p
```

Logical [negation](https://en.wikipedia.org/wiki/Negation) operator.

`¬` can be typed by `\neg[TAB]`.

# Examples

```jldoctest
julia> @atomize print_table(¬p)
┌───┬────┐
│ p │ ¬p │
├───┼────┤
│ ⊤ │ ⊥  │
│ ⊥ │ ⊤  │
└───┴────┘
```
