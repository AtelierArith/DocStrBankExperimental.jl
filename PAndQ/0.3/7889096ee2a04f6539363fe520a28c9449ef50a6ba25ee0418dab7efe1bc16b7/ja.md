```
not_exclusive_or(p, q)
p ↔ q
```

論理的[排他的非選言](https://en.wikipedia.org/wiki/Logical_biconditional)演算子。

`↔`は`\leftrightarrow[TAB]`で入力できます。

# 例

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
