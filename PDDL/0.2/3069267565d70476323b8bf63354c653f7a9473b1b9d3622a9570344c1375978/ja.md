```
satisfiers(domain::Domain, state::State, term::Term)
satisfiers(domain::Domain, state::State, terms::AbstractVector{<:Term})
```

指定された `domain` と `state` 内でクエリされた `term` または `terms` の満たす置換のリストを返します。
