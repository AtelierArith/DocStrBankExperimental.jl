```
Unique(X) :: Query
```

This query produces all distinct elements emitted by `X`.

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

In the query form, `Unique` produces all distinct elements of its input.

```jldoctest
julia> unitknot[Lift(['a','b','b','c','c','c']) >> Unique]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```
