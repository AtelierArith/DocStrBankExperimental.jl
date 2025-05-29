```
calculate_shared_production(ECModel::AbstractEC; per_unit::Bool=true)
```

Calculate the energy that each user produces and uses in its own POD or it is commercially consumed within the EC, when creaded. When only*shared is false, also self production is considered, otherwise only shared energy. Output is normalized with respect to the demand when per*unit is true

''' Outputs –––- shared*cons*frac : DenseAxisArray     Shared consumption for each user and the aggregation '''
