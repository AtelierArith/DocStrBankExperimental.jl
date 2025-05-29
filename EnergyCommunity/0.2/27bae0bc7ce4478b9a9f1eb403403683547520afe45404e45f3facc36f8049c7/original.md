```
calculate_grid_import(::AbstractGroupCO, ECModel::AbstractEC; per_unit::Bool=true)
```

Calculate grid usage for the Cooperative case. Output is normalized with respect to the demand when per*unit is true ''' Outputs –––- grid*frac : DenseAxisArray     Reliance on the grid demand for each user and the aggregation '''
