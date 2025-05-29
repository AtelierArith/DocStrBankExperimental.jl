```
satisfy(domain::Domain, state::State, term::Term)
satisfy(domain::Domain, state::State, terms::AbstractVector{<:Term})
```

Returns whether the queried `term` or `terms` can be satisfied in the given `domain` and `state`.
