```
Sum(X) :: Query
```

In the combinator form, `Sum(X)` emits the sum of elements produced by `X`.

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[Sum(X)]
┼───┼
│ 6 │
```

The `Sum` of an empty input is `0`.

```jldoctest
julia> unitknot[Sum(Int[])]
┼───┼
│ 0 │
```

---

```
Each(X >> Sum) :: Query
```

In the query form, `Sum` emits the sum of input elements.

```jldoctest
julia> X = Lift(1:3);

julia> unitknot[X >> Sum]
┼───┼
│ 6 │
```
