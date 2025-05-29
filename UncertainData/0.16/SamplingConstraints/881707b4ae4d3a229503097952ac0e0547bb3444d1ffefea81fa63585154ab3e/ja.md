```
constrain(udata::Vector{<:AbstractUncertainValue}, 
	constraints::Vector{T}) where {T<:SamplingConstraint} -> Vector{<:AbstractUncertainValue}
```

`udata`の各不確実値に異なるサンプリング制約を適用することによって、不確実値のベクトルを返します。
