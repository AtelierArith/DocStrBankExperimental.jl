```
refarray(x::LabeledArray)
refarray(x::SubArray{<:Any, <:Any, <:LabeledArray})
refarray(x::Base.ReshapedArray{<:Any, <:Any, <:LabeledArray})
refarray(x::SubArray{<:Any, <:Any, <:Base.ReshapedArray{<:Any, <:Any, <:LabeledArray}})
```

[`LabeledArray`](@ref)の背後にある値の配列を返します。
