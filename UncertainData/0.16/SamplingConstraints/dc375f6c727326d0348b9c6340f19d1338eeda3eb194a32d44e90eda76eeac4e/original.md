```
constrain(udata::UncertainDataset, 
	constraints::Vector{T}) where {T<:SamplingConstraint} -> ConstrainedUncertainDataset
```

Return a uncertain dataset by applying a different sampling constraint to each uncertain  value in `udata`.
