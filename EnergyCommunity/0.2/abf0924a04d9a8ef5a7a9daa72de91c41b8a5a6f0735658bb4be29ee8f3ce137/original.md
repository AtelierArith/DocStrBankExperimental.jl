```
to_objective_callback_by_subgroup(::AbstractGroupANC, ECModel::AbstractEC)
```

Function that returns a callback function that quantifies the objective of a given subgroup of users The returned function objective_func accepts as arguments an AbstractVector of users and returns the objective of the aggregation for Aggregated Non Cooperative models

## Parameters

ECModel : AbstractEC     Cooperative EC Model of the EC to study.     When the model is not cooperative an error is thrown. base_model : AbstractEC optional     When provided, it represents the base model used to perform the calculations

## Return

objective*callback*by_subgroup : Function     Function that accepts as input an AbstractVector (or Set) of users and returns     as output the benefit of the specified community
