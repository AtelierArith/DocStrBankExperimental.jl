```
execute(domain::Domain, state::State, action::Action, args)
execute(domain::Domain, state::State, action::Term)
```

Execute an `action` parameterized by `args` in the given `state`, returning the resulting state.  Action parameters can also be specified as the arguments of a compound `Term`.
