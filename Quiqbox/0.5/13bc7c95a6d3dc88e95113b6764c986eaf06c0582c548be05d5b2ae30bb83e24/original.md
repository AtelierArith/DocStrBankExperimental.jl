```
assignCenInVal!(b::FloatingGTBasisFuncs{T, D}, center::AbstractVector{<:Real}) -> 
SpatialPoint{T, D}
```

Change the input value of the `ParamBox` stored in `b.center` (meaning the output value  will also change according to the mapping function). Then, return the altered center.
