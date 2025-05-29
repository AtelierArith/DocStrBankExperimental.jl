```
resample(udata::UncertainIndexValueDataset, 
	constraint::Union{SamplingConstraint, Vector{SamplingConstraint}},
	n::Int) -> Tuple{Vector{Float64}, Vector{Float64}}
```

Resample `n` realizations of an uncertain index-value dataset in an element-wise manner. 

Enforces the provided sampling `constraint` to all uncertain values in the dataset, both  indices and data values.

If a single constraint is provided, that constraint will be applied to all values. If a  vector of constraints (as many as there are values) is provided, then the constraints are  applied element-wise to both the indices and the data values.
