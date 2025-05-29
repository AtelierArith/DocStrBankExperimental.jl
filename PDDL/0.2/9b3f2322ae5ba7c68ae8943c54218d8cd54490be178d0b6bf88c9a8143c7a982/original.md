```
GroundAction(name, term, preconds, effect)
```

Ground action definition, represented by the `name` of its corresponding action schema, a `term` with grounded arguments, a list of `preconds`, and an `effect`, represented as a [`PDDL.GenericDiff`](@ref) or [`PDDL.ConditionalDiff`](@ref).
