```
calculate_shared_consumption(::AbstractGroupNC, ECModel::AbstractEC; kwargs...)
```

Calculate the demand that each user meets using its own sources or other users for the Non-Cooperative case. In the Non-Cooperative case, there is no shared energy, only self consumption. Shared energy means energy that is shared between  Output is normalized with respect to the demand when per_unit is true

''' Outputs –––- shared*cons*frac : DenseAxisArray     Shared consumption for each user and the aggregation '''
