```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

Resample an uncertain index-value dataset in an element-wise manner. 

Enforces a unique sampling constraint `constraint_idxs[i]` to the i-th index value,  while using the same sampling constraint `constraint_vals` on all data values.
