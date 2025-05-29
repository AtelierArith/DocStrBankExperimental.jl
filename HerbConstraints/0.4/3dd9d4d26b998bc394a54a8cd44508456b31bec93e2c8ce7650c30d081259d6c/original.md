```
LocalUnique <: AbstractLocalConstraint
```

Enforces that a given `rule` appears at or below the given `path` at most once. In case of the UniformSolver, cache the list of `holes`, since no new holes can appear.
