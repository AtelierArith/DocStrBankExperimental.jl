```
execute!(domain::Domain, state::State, action::Action, args)
execute!(domain::Domain, state::State, action::Term)
```

Variant of [`execute`](@ref) that modifies `state` in-place.
