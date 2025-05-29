```
relevant(domain::Domain, state::State, action::Action, args)
relevant(domain::Domain, state::State, action::Term)
```

Check if an `action` parameterized by `args` is relevant (can lead to) a `state` in the given `domain`. Action parameters can also be specified as the arguments of a compound `Term`.
