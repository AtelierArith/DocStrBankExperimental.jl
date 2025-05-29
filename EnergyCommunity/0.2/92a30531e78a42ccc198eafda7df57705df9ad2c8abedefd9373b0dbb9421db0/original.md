```
to_objective_callback_by_subgroup(ECModel::AbstractEC)
```

Function that returns a callback function that quantifies the objective of a given subgroup of users The returned function objective_func accepts as arguments an AbstractVector of users and returns the objective of the aggregation for any model

## Parameters

ECModel : AbstractEC     Cooperative EC Model of the EC to study.     When the model is not cooperative an error is thrown.

## Return

objective*callback*by_subgroup : Function     Function that accepts as input an AbstractVector (or Set) of users and returns     as output the benefit of the specified community
