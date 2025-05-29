```
Exists(X) :: Query
```

In the combinator form, `Exists(X)` emits a boolean testing if `X` produces any elements.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[Exists(X)]
┼──────┼
│ true │
```

When the query argument `X` is empty, `Exists(X)` produces `false`.

```jldoctest
julia> X = Lift([]);

julia> unitknot[Exists(X)]
┼───────┼
│ false │
```

---

```
Each(X >> Exists) :: Query
```

In the query form, `Exists` emits a boolean testing if its input has any elements.

```jldoctest
julia> X = Lift('a':'c');

julia> unitknot[X >> Exists]
┼──────┼
│ true │
```

When the query input is empty, `Exists` produces `false`.

```jldoctest
julia> X = Lift([]);

julia> unitknot[X >> Exists]
┼───────┼
│ false │
```
