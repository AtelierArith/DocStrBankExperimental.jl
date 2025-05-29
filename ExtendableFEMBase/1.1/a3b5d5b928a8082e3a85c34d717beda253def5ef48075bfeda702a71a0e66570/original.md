```
function integrate_segment!(
	result::Array{T,1},
	SI::SegmentIntegrator,
	w::Array{Array{T,1},1},
	b::Array{Array{T,1},1},
	item
	) where {T}
```

Integrate a segment with world coordinates w and barycentric coordinates b in the cell with the given item number.
