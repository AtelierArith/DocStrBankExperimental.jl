```
update_partable!(partable::AbstractParameterTable, param_labels::Vector{Symbol}, params, column)
```

Write parameter `values` into `column` of `partable`.

The `param_labels` and `params` vectors define the pairs of  parameters, which are being matched to the `:param` column of the `partable`.
