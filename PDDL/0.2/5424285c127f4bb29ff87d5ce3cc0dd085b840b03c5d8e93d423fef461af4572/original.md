```
evaluate(domain::Domain, state::State, term::Term)
```

Evaluates a grounded `term` in the given `domain` and `state`. If `term` refers to a numeric fluent, the value of the fluent is returned. For logical predicates, `evaluate` is equivalent to `satisfy`.
