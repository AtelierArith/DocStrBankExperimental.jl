```
FEVector{T}(FES; name = nothing, tags = nothing, kwargs...) where T <: Real
```

Creates FEVector that has one block if FES is a single FESpace, and a blockwise FEVector if FES is a vector of FESpaces. Optionally a name for the vector (as a String) or each of the blocks (as a vector of Strings), or tags (as an Array{Any}) for the blocks can be specified.
