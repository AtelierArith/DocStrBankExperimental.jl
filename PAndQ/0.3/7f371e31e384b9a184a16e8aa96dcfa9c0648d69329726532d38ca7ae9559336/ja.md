```
not_converse_imply(p, q)
p ↚ q
```

論理 [逆非含意](https://en.wikipedia.org/wiki/Converse_nonimplication) 演算子。

`↚` は `\nleftarrow[TAB]` で入力できます。

# 例

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
