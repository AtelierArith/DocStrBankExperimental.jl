```
calculate_self_consumption(ECModel::AbstractEC; per_unit::Bool=true)
```

Calculate the demand that each user meets using its own sources, or self consumption. Output is normalized with respect to the demand when per_unit is true

''' Outputs –––- shared*cons*frac : DenseAxisArray     Shared consumption for each user and the aggregation '''
