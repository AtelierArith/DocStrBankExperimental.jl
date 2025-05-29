```
constrain(udata::UncertainIndexDataset, 
    constraints::Vector{T}) where {T<:SamplingConstraint} -> ConstrainedUncertainIndexDataset
```

Return a uncertain dataset by applying a different sampling constraint to each uncertain  value in `udata`.
