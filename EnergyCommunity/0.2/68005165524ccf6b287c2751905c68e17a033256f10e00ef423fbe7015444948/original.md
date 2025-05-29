```
calculate_production_shares(ECModel::AbstractEC; per_unit::Bool=true)
```

Calculate energy ratio by energy production resource for a generic group Output is normalized with respect to the demand when per_unit is true '''

# Outputs

frac : DenseAxisArray     DenseAxisArray describing the share of energy production by     energy resource by user and the entire system,     normalized with respect to the demand of the corresponding group

'''
