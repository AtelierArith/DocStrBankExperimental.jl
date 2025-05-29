```
relabel(covar::CovarianceMatrix, mapping::Dict{Symbol,Symbol})
```

This relabels a CovarianceMatrix struct to give all the assets alternative names.

### Inputs

  * `covar` - The `CovarianceMatrix` object you want to relabel.
  * `mapping` - A dict mapping from the names you have to the names you want.

### Returns

  * A `CovarianceMatrix` the same as the one you input but with new labels.
