```
Count(X) :: Query
```

In the combinator form, `Count(X)` emits the number of elements produced by `X`.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Count(X)]
┼───┼
│ 3 │
```

---

```
Each(X >> Count) :: Query
```

In the query form, `Count` emits the number of elements in its input.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> Count]
┼───┼
│ 3 │
```

To limit the scope of aggregation, use `Each`.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Lift(1:3) >> Each(X >> Count)]
──┼───┼
1 │ 3 │
2 │ 3 │
3 │ 3 │
```
