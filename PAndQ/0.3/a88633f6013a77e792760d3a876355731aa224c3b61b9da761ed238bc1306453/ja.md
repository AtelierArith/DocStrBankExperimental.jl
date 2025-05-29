```
not_imply(p, q)
p ↛ q
```

論理的[非含意](https://en.wikipedia.org/wiki/Material_nonimplication)演算子。

`↛`は`\nrightarrow[TAB]`で入力できます。

# 例

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
