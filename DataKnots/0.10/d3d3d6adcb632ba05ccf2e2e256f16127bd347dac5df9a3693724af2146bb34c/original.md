```
 Max(X) :: Query
```

In the combinator form, `Max(X)` finds the maximum among the elements produced by `X`.

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[Max(X)]
┼───┼
│ 3 │
```

The `Max` of an empty input is empty.

```jldoctest
julia> unitknot[Max(Int[])]
(empty)
```

---

```
Each(X >> Max) :: Query
```

In the query form, `Max` finds the maximum of its input elements.

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[X >> Max]
┼───┼
│ 3 │
```
