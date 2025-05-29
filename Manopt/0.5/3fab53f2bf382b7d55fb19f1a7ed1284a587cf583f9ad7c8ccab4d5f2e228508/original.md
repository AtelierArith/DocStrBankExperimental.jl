```
RecordEntryChange{T} <: RecordAction
```

record a certain entries change during iterates

# Additional fields

  * `recorded_values` : the recorded Iterates
  * `field`           : Symbol the field can be accessed with within [`AbstractManoptSolverState`](@ref)
  * `distance`        : function (p,o,x1,x2) to compute the change/distance between two values of the entry
  * `storage`         : a [`StoreStateAction`](@ref) to store (at least) `getproperty(o, d.field)`

# Constructor

```
RecordEntryChange(f::Symbol, d, a::StoreStateAction=StoreStateAction([f]))
```
