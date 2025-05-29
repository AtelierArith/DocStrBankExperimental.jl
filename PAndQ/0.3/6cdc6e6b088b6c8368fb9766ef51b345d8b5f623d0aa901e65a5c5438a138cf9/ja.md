```
converse_imply(p, q)
p ← q
```

論理 [逆含意](https://en.wikipedia.org/wiki/Converse_(logic)#Implicational_converse) 演算子。

`←` は `\leftarrow[TAB]` で入力できます。

# 例

```jldoctest
julia> @atomize print_table(p ← q)
┌───┬───┬───────┐
│ p │ q │ p ← q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊤     │
│ ⊥ │ ⊤ │ ⊥     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊤     │
│ ⊥ │ ⊥ │ ⊤     │
└───┴───┴───────┘
```
