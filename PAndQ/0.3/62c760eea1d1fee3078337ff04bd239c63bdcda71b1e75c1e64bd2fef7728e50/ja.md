```
imply(p, q)
p → q
```

論理的[含意](https://en.wikipedia.org/wiki/Material_conditional)演算子。

`→`は`\rightarrow[TAB]`で入力できます。

# 例

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
