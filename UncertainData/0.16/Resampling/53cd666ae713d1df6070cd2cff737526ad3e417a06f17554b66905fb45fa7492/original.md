```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::SamplingConstraint, 
	constraint_vals::SamplingConstraint,
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

Resample `n` realizations of an uncertain index-value dataset in an element-wise manner. 

Enforces the same sampling constraint `constraint_idxs` to all index values, and the  `constraint_vals` sampling constraint to all data values.
