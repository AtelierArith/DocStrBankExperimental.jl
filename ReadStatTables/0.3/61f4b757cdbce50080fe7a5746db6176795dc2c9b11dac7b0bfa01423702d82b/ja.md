```
getvaluelabels(x::LabeledArray)
getvaluelabels(x::SubArray{<:Any, <:Any, <:LabeledArray})
getvaluelabels(x::Base.ReshapedArray{<:Any, <:Any, <:LabeledArray})
getvaluelabels(x::SubArray{<:Any, <:Any, <:Base.ReshapedArray{<:Any, <:Any, <:LabeledArray}})
```

`x`に付随する値ラベルの辞書を返します。
