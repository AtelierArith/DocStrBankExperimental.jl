```
calculate_self_production(ECModel::AbstractEC; per_unit::Bool=true, only_shared::Bool=false)
```

Calculate the self production for each user. Output is normalized with respect to the demand when per_unit is true

''' Outputs –––- shared*en*frac : DenseAxisArray     Shared energy for each user and the aggregation '''
