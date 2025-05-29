```
not_or(p, q)
p ↓ q
```

論理[非選言](https://en.wikipedia.org/wiki/Logical_NOR)演算子。

`↓`は`\downarrow[TAB]`で入力できます。

# 例

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
