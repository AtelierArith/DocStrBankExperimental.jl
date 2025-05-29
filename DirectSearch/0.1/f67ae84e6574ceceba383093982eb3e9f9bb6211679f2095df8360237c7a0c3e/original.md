```
AddProgressiveConstraint(p::AbstractProblem, c::Function; index::CollectionIndex=CollectionIndex(2))
```

Register a single function that defines a progressive barrier constraint. Return an index that refers to the constraint.

The provided function should take a vector input and return a numeric value indicating if the constraint has been met or not. Less than or equal to 0 indicates the constraint has been met. 0 shows the constraint has been violated.

The `index` argument can be specified to give a collection to add the constraint to. The specified collection must exist, and must be able to accept progressive barrier constraints. If `index` is not specified then it is added to collection 2, the default progressive barrier constraint collection.
