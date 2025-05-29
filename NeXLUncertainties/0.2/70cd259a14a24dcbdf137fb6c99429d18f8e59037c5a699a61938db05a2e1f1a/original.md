```
estimated(labels::Vector{<:Label}, samples::Matrix{Float64})
```

Estimate an UncertainValues based on a set of samples ('measurements'). Computes the mean values and the covariance matrix from the expectation values. Each row `r` in samples represents a measured quantity as identified by `labels[r]`. Each column represents a single set of measurements of all the labeled quantities.
