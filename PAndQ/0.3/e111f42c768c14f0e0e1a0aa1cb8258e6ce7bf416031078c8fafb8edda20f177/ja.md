```
not(p)
¬p
```

論理的[否定](https://en.wikipedia.org/wiki/Negation)演算子。

`¬`は`\neg[TAB]`で入力できます。

# 例

```jldoctest
julia> @atomize print_table(¬p)
┌───┬────┐
│ p │ ¬p │
├───┼────┤
│ ⊤ │ ⊥  │
│ ⊥ │ ⊤  │
└───┴────┘
```
