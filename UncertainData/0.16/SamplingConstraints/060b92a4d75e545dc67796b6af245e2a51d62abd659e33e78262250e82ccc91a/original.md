```
constrain(udata::AbstractUncertainValueDataset, 
	s::SamplingConstraint) -> ConstrainedUncertainValueDataset
```

Return a uncertain dataset by applying the constraint `s` to each uncertain value in `udata`.
