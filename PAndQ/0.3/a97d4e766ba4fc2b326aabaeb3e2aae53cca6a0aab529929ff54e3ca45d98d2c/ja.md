```
not_and(p, q)
p ↑ q
```

論理[非結合](https://en.wikipedia.org/wiki/Sheffer_stroke)演算子。

`↑`は`\uparrow[TAB]`で入力できます。

# 例

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
