```
AbstractCellRange
```

Defines a range of cells within a [`Domain`](@ref).

# Fields

All implementations should define:

  * `domain::Domain`: the [`Domain`](@ref) covered by this cellrange.
  * `operatorID::Int`: If `operatorID==0`, call all `Reaction`s, otherwise only call those with matching `operatorID` (this enables operator splitting).
  * `indices`: an iterable list of cell indices.

And then may provide subtype-specific fields defining additional ranges of cells.
