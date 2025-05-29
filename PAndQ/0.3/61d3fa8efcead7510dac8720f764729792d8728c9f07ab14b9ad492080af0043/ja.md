```
and(p, q)
p ∧ q
```

論理的[結合](https://en.wikipedia.org/wiki/Logical_conjunction)演算子。

`∧`は`\wedge[TAB]`で入力できます。

# 例

```jldoctest
julia> @atomize print_table(p ∧ q)
┌───┬───┬───────┐
│ p │ q │ p ∧ q │
├───┼───┼───────┤
│ ⊤ │ ⊤ │ ⊤     │
│ ⊥ │ ⊤ │ ⊥     │
├───┼───┼───────┤
│ ⊤ │ ⊥ │ ⊥     │
│ ⊥ │ ⊥ │ ⊥     │
└───┴───┴───────┘
```
