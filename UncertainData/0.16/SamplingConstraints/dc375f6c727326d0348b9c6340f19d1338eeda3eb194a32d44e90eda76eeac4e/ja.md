```
constrain(udata::UncertainDataset, 
	constraints::Vector{T}) where {T<:SamplingConstraint} -> ConstrainedUncertainDataset
```

`udata`の各不確実な値に異なるサンプリング制約を適用することによって、不確実なデータセットを返します。
