```
LocalForbiddenSequence <: AbstractLocalConstraint
```

Forbids the given `sequence` of rule nodes ending at the node at the `path`. If any of the rules in `ignore_if` appears in the sequence, the constraint is ignored.
