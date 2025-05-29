```
heterogeneity(ffrs::Vector{FilterFitResult}, lbl::ReferenceLabel)
```

Computes the ratio of the standard deviation of the measured values over the mean calculated uncertainty from the fit.  A value near 1 means the sample appears homogeneous and a value greater than 1 means the sample appears heterogeneous.
