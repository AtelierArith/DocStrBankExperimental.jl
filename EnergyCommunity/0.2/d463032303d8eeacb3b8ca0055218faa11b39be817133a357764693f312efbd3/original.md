```
calculate_grid_export(::AbstractGroupNC, ECModel::AbstractEC; per_unit::Bool=true)
```

Calculate grid export for the Non-Cooperative case Output is normalized with respect to the demand when per_unit is true

''' Outputs –––- grid_frac : DenseAxisArray     Reliance on the grid demand for each user and the aggregation '''
