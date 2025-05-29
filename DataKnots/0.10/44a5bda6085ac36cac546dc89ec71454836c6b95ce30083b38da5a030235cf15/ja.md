```
Tag(name::Symbol, F) :: Query
```

これはクエリの代替名を提供します。

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

これはクエリコンビネータの代替名を提供します。

```jldoctest
julia> Inc(X) = Lift(+, (X, 1));

julia> Inc(It)
Lift(+, (It, 1))

julia> Inc(X) = Tag(:Inc, (X,), Lift(+, (X, 1)));

julia> Inc(It)
Inc(It)
```
