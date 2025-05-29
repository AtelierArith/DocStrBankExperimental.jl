```
First(X) :: Query
```

In the combinator form, `First(X)` emits the first element produced by its argument `X`.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[First(X)]
┼───┼
│ a │
```

---

```
Each(X >> First) :: Query
```

In the query form, `First` emits the first element of its input.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> First]
┼───┼
│ a │
```
