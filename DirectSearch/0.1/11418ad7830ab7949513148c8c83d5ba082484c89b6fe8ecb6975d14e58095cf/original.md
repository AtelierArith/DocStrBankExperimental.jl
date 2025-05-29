```
AddExtremeConstraint(p::AbstractProblem, c::Function
                     index::CollectionIndex=CollectionIndex(1)
                    )::ConstraintIndex where T
```

Register a single function that defines an extreme barrier constraint. Return a constraint index.

The provided function should take a vector input and return a boolean or numeric value indicating if the constraint has been met or not. `true` or less than or equal to 0 indicates the constraint has been met. `false` or greater than 0 shows the constraint has been violated.

The `index` argument can be specified to give a collection to add the constraint to. The specified collection must exist, and must be able to accept extreme barrier constraints. If `index` is not specified then it is added to collection 1, the default extreme constraint collection.
