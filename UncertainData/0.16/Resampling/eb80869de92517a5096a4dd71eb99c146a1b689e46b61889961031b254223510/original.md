```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Union{SamplingConstraint, Vector{SamplingConstraint}}, 
	constraint_vals::Union{SamplingConstraint, Vector{SamplingConstraint}}) -> Tuple{Vector{Float64}, Vector{Float64}}
```

Resample an uncertain index-value dataset in an element-wise manner. 

Enforces separate sampling constraints to the indices and to the data values. 

If a single constraint is provided, that constraint will be applied to all values. If a  vector of constraints (as many as there are values) is provided, then the constraints are  applied element-wise.
