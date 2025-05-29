```
satisfiers(domain::Domain, state::State, term::Term)
satisfiers(domain::Domain, state::State, terms::AbstractVector{<:Term})
```

Returns a list of satisfying substitutions of the queried `term` or `terms` within the given `domain` and `state`.
