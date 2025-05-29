```
regress(domain::Domain, state::State, action::Action, args)
regress(domain::Domain, state::State, action::Term)
```

Compute the pre-image of an `action` parameterized by `args` with respect to a `state`. Action parameters can also be specified as the arguments of a compound `Term`.
