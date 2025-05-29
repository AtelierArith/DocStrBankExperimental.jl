```
or(p, q)
p ∨ q
```

論理的[選言](https://en.wikipedia.org/wiki/Logical_disjunction)演算子。

`∨`は`\vee[TAB]`で入力できます。

# 例

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
