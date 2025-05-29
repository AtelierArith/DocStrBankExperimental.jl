```
constrain(udata::Vector{<:AbstractUncertainValue}, 
	s::SamplingConstraint) -> ConstrainedUncertainValueDataset
```

Return a vector of uncertain value by applying the constraint `s` to each uncertain value in `udata`.
