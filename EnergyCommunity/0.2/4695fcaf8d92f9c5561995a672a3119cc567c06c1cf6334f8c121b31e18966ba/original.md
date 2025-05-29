```
calculate_shared_consumption(::AbstractGroupANC, ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

Calculate the demand that each user meets using its own sources or other users for the Aggregated Non Cooperative case. In this case, there can be shared energy, non only self consumption. When only*shared is false, also self consumption is considered, otherwise only shared energy. Shared energy means energy that is shared between  Output is normalized with respect to the demand when per*unit is true

''' Outputs –––- shared*cons*frac : DenseAxisArray     Shared consumption for each user and the aggregation '''
