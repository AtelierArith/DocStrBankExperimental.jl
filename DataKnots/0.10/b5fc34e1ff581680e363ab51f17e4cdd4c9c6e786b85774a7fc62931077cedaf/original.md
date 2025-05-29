```
 Min(X) :: Query
```

In the combinator form, `Min(X)` finds the minimum among the elements produced by `X`.

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[Min(X)]
┼───┼
│ 1 │
```

The `Min` of an empty input is empty.

```jldoctest
julia> unitknot[Min(Int[])]
(empty)
```

---

```
Each(X >> Min) :: Query
```

In the query form, `Min` finds the minimum of its input elements.

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[X >> Min]
┼───┼
│ 1 │
```
