```
regress!(domain::Domain, state::State, action::Action, args)
regress!(domain::Domain, state::State, action::Term)
```

Variant of [`regress`](@ref) that modifies `state` in-place.
