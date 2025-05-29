```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint,
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

Resample `n` realizations of an uncertain index-value dataset in an element-wise manner. 

Enforces the same sampling constraint `constraint_idxs` on all index values,  while using the sampling constraint `constraint_vals[i]` to the i-th data value.
