```
dyup(
	arr::Array{T,3},
	dz::Vector{T}, 
	periodic::Bool=false, 
	order::Int=6
	)
```

`arr` のすべてのエントリの y 方向の空間微分を、半グリッドポイント上にシフトして計算します。デフォルトでは、`order=6` の 6 次精度の Bifrost 微分が使用され、キーワード `order=2` を使用することで 2 次精度の微分もオプションで利用可能です。
