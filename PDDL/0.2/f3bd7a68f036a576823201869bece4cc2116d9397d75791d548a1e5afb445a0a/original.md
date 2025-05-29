```
transition(domain::Domain, state::State, action::Term)
transition(domain::Domain, state::State, actions)
```

Returns the successor to `state` in the given `domain` after applying a single `action` or a set of `actions` in parallel.
