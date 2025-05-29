```
to_utility_callback_by_subgroup(ECModel::AbstractEC, base_group_type::AbstractGroup)
```

Function that returns a callback function that quantifies the benefit of a given subgroup of users The returned function utility_func accepts as arguments an AbstractVector of users and returns the benefit with respect to the base case of the users optimized independently

## Parameters

ECModel : AbstractEC     Cooperative EC Model of the EC to study.     When the model is not cooperative an error is thrown. base*group*type : AbstractGroup     Type of the base case to consider no*aggregator*group : AbstractGroup (otional, default NonCooperative)     EC group type for when no aggregator is considered

## Return

utility*callback*by_subgroup : Function     Function that accepts as input an AbstractVector (or Set) of users and returns     as output the benefit of the specified community
