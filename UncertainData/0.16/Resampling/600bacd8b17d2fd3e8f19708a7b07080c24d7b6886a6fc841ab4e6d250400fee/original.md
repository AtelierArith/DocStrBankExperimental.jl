```
resample(udata::UncertainIndexValueDataset, 
	constraint::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

Resample an uncertain index-value dataset element-wise in an element-wise manner.

Enforces the provided sampling `constraint` to all uncertain values in the dataset, both  indices and data values.
