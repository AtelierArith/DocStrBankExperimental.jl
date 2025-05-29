```
ground(domain::Domain, state::State, action::Action, args)
```

Return ground action given a lifted `action` and action `args`. If the action is never satisfiable given the `domain` and `state`, return `nothing`.
