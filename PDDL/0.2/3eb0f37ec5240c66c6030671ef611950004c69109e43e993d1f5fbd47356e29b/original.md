```
available(domain::Domain, state::State, action::Action, args)
available(domain::Domain, state::State, action::Term)
```

Check if an `action` parameterized by `args` can be executed in the given `state` and `domain`. Action parameters can also be specified as the arguments of a compound `Term`.
