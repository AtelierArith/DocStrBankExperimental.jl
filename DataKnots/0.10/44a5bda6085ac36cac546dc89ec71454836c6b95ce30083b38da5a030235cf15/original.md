```
Tag(name::Symbol, F) :: Query
```

This provides a substitute name for a query.

```jldoctest
julia> IncIt = It .+ 1
It .+ 1

julia> IncIt = Tag(:IncIt, It .+ 1)
IncIt
```

---

```
Tag(name::Symbol, (X₁, X₂ … Xₙ), F) :: Query
```

This provides a substitute name for a query combinator.

```jldoctest
julia> Inc(X) = Lift(+, (X, 1));

julia> Inc(It)
Lift(+, (It, 1))

julia> Inc(X) = Tag(:Inc, (X,), Lift(+, (X, 1)));

julia> Inc(It)
Inc(It)
```
