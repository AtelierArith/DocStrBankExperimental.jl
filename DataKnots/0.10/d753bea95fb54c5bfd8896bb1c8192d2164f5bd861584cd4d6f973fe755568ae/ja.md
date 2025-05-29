```
Unique(X) :: Query
```

このクエリは、`X`によって発生するすべての異なる要素を生成します。

```jldoctest
julia> unitknot[Unique(['a','b','b','c','c','c'])]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

---

```
Each(X >> Unique) :: Query
```

クエリ形式では、`Unique`はその入力のすべての異なる要素を生成します。

```jldoctest
julia> unitknot[Lift(['a','b','b','c','c','c']) >> Unique]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```
