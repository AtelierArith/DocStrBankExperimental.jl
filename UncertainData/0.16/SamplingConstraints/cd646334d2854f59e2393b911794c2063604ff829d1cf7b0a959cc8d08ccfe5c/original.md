```
constrain(udata::AbstractUncertainValueDataset, 
	constraints::Vector{T}) where {T<:SamplingConstraint} -> ConstrainedUncertainValueDataset
```

Return a uncertain dataset by applying a different sampling constraint to each uncertain  value in `udata`.
