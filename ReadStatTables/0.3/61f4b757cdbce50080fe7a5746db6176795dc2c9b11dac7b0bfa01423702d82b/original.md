```
getvaluelabels(x::LabeledArray)
getvaluelabels(x::SubArray{<:Any, <:Any, <:LabeledArray})
getvaluelabels(x::Base.ReshapedArray{<:Any, <:Any, <:LabeledArray})
getvaluelabels(x::SubArray{<:Any, <:Any, <:Base.ReshapedArray{<:Any, <:Any, <:LabeledArray}})
```

Return the dictionary of value labels attached to `x`.
