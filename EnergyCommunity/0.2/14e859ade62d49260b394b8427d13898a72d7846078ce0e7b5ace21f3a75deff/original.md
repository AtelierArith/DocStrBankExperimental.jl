```
calculate_shared_consumption(ECModel::AbstractEC; per_unit::Bool=true)
```

Calculate the demand that each user meets using its own sources or other users. When only*shared is false, also self consumption is considered, otherwise only shared consumption. Output is normalized with respect to the demand when per*unit is true

''' Outputs –––- shared*cons*frac : DenseAxisArray     Shared consumption for each user and the aggregation '''
