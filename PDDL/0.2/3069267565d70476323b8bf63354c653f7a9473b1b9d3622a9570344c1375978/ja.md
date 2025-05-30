```
satisfiers(domain::Domain, state::State, term::Term)
satisfiers(domain::Domain, state::State, terms::AbstractVector{<:Term})
```

与えられた `domain` と `state` 内でクエリされた `term` または `terms` の満たす置換のリストを返します。
