```
Last(X) :: Query
```

In the combinator form, `Last(X)` emits the last element produced by its argument `X`.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Last(X)]
┼───┼
│ c │
```

---

```
Each(X >> Last) :: Query
```

In the query form, `Last` emits the last element of its input.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> Last]
┼───┼
│ c │
```
