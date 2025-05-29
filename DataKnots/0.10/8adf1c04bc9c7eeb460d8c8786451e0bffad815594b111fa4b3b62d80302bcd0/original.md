```
Nth(X, N) :: Query
```

In the combinator form, `Nth(X, N)` emits the `N`th element produced by its argument `X`.

```jldoctest
julia> X = Lift('a':'d');

julia> N = Count(X) .÷ 2;

julia> unitknot[Nth(X, N)]
┼───┼
│ b │
```

---

```
Each(X >> Nth(N)) :: Query
```

In the query form, `Nth(N)` emits the `N`th element produced by its input.

```jldoctest
julia> X = Lift('a':'d');

julia> N = Count(X) .÷ 2;

julia> unitknot[X >> Nth(N)]
┼───┼
│ b │
```
