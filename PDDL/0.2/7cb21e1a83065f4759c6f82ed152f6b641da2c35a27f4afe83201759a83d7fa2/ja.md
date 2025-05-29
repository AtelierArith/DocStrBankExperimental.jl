```
satisfy(domain::Domain, state::State, term::Term)
satisfy(domain::Domain, state::State, terms::AbstractVector{<:Term})
```

与えられた `domain` と `state` で、クエリされた `term` または `terms` が満たされるかどうかを返します。
