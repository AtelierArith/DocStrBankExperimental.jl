```
workingweights(m::RobustLinearModel)
```

The robust weights computed by the model.

This can be used to detect outliers, as outliers weights are lower than the weights of valid data points.
