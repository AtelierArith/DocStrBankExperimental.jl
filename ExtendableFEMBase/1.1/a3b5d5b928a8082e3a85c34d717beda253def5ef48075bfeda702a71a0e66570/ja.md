```
function integrate_segment!(
	result::Array{T,1},
	SI::SegmentIntegrator,
	w::Array{Array{T,1},1},
	b::Array{Array{T,1},1},
	item
	) where {T}
```

与えられたアイテム番号のセル内で、ワールド座標 w とバリセントリック座標 b を使用してセグメントを統合します。
