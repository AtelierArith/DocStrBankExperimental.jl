```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint) -> Tuple{Vector{Float64}, Vector{Float64}}
```

Resample an uncertain index-value dataset in an element-wise manner. 

Enforces a unique sampling constraint `constraint_idxs[i]` to the i-th index value.  Also enforces a unique sampling constraint `constraint_vals[i]` to the i-th data value.
