```
calculate_shared_production(::AbstractGroupCO, ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

Calculate the shared produced energy for the Cooperative case. In the Cooperative case, there can be shared energy between users, not only self production. When only*shared is false, also self production is considered, otherwise only shared energy. Shared energy means energy that is shared between  Output is normalized with respect to the demand when per*unit is true

''' Outputs –––- shared*en*frac : DenseAxisArray     Shared energy for each user and the aggregation '''
