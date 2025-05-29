```
dydn(
	arr::Array{T,3},
	dz::Vector{T}, 
	periodic::Bool=false, 
	order::Int=6
	)
```

Computes the spatial derivative in the y-direction of every entry in `arr`  shifted a half grid point downwards. Defaults to the 6th order accurate Bifrost  derivative with `order=6`, optional 2nd order accurate derivative with keyword  `order=2`
