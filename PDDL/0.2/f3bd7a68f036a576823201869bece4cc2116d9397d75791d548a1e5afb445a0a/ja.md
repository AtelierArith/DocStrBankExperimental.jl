```
transition(domain::Domain, state::State, action::Term)
transition(domain::Domain, state::State, actions)
```

与えられた `domain` において、単一の `action` または並行して適用される `actions` のセットを適用した後の `state` の後継を返します。
