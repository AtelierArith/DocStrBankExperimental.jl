```
resample(udata::UncertainIndexValueDataset, 
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

Resample `n` realizations an uncertain index-value dataset in an element-wise manner. 

Enforces the provided sampling `constraint` to all uncertain values in the dataset, both  indices and data values.
