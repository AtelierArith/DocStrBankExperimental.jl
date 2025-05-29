```
transition!(domain::Domain, state::State, action::Term)
transition!(domain::Domain, state::State, actions)
```

Variant of [`transition`](@ref) that modifies `state` in place.
