```
dxdn(
	arr::Array{T,3},
	dz::Vector{T}, 
	periodic::Bool=false, 
	order::Int=6
	)
```

`arr` のすべてのエントリの x 方向の空間微分を計算し、半グリッドポイント下にシフトします。デフォルトでは、`order=6` の 6 次精度の Bifrost 微分を使用し、キーワード `order=2` を使用することで 2 次精度の微分もオプションで利用できます。
