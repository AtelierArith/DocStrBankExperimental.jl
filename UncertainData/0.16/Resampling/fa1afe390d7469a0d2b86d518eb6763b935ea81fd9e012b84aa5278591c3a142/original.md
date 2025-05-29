```
resample(udata::UncertainIndexValueDataset, 
	constraint_idxs::Vector{SamplingConstraint}, 
	constraint_vals::SamplingConstraint,
	n::Int) -> Vector{Tuple{Vector{Float64}, Vector{Float64}}}
```

Resample `n` realizations of an uncertain index-value dataset in an element-wise manner. 

Enforces a unique sampling constraint `constraint_idxs[i]` to both the i-th index value  and to the i-th data value. 
