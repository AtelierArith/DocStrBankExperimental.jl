```
abstract type CombinatorialObjective
```

A specific objective function for a combinatorial problem. In general, the  objective is to either minimise or maximise the natural objective function,  but more specific objectives can be provided with other subtypes.

Objects of type `CombinatorialObjective` are supposed to be given as arguments when building a `CombinatorialInstance`. In any case,  `objective(::CombinatorialInstance)` can be used to retrieve the objective of  an instance.
