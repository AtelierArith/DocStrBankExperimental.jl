```
initstate(domain::Domain, problem::Problem)
initstate(domain::Domain, objtypes[, fluents])
```

Construct the initial state for a given planning `domain` and `problem`, or from a `domain`, a map of objects to their types (`objtypes`), and an optional list of `fluents`.

Fluents can either be provided as a list of `Term`s representing the initial fluents in a PDDL problem, or as a map from fluent names to fluent values.
