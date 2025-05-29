```
get_confidence_hypercube(covar::ForwardCovariance, confidence_level::Real, data::Array{T,2}; tuning_parameter::Real = 1.0)
```

This returns the endpoints of a hypercube that contains confidence_level (%) of the dataset.
