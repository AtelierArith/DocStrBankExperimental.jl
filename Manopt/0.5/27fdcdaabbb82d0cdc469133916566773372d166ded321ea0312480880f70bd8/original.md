```
StopWhenEntryChangeLess
```

Evaluate whether a certain fields change is less than a certain threshold

## Fields

  * `field`:     a symbol addressing the corresponding field in a certain subtype of [`AbstractManoptSolverState`](@ref) to track
  * `distance`:  a function `(problem, state, v1, v2) -> R` that computes the distance between two possible values of the `field`
  * `storage`:   a [`StoreStateAction`](@ref) to store the previous value of the `field`
  * `threshold`: the threshold to indicate to stop when the distance is below this value

# Internal fields

  * `at_iteration`: store the iteration at which the stop indication happened

stores a threshold when to stop looking at the norm of the change of the optimization variable from within a [`AbstractManoptSolverState`](@ref), i.e `get_iterate(o)`. For the storage a [`StoreStateAction`](@ref) is used

# Constructor

```
StopWhenEntryChangeLess(
    field::Symbol
    distance,
    threshold;
    storage::StoreStateAction=StoreStateAction([field]),
)
```
