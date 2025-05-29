```
exclusive_or(p, q)
p ↮ q
```

論理 [排他的論理和](https://en.wikipedia.org/wiki/Exclusive_or) 演算子。

`↮` は `\nleftrightarrow[TAB]` で入力できます。

# 例

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
