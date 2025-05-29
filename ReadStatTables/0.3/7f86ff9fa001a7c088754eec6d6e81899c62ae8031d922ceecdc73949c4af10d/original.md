```
refarray(x::LabeledArray)
refarray(x::SubArray{<:Any, <:Any, <:LabeledArray})
refarray(x::Base.ReshapedArray{<:Any, <:Any, <:LabeledArray})
refarray(x::SubArray{<:Any, <:Any, <:Base.ReshapedArray{<:Any, <:Any, <:LabeledArray}})
```

Return the array of values underlying a [`LabeledArray`](@ref).
