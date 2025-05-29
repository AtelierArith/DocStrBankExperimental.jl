```
constrain(udata::Vector{<:AbstractUncertainValue}, 
	constraints::Vector{T}) where {T<:SamplingConstraint} -> Vector{<:AbstractUncertainValue}
```

Return a vector of uncertain values by applying a different sampling constraint to each uncertain  value in `udata`.
