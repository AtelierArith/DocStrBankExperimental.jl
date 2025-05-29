```
batch(
	detector_info_array::Matrix{S},
	srcHeights_array::Vector{S},
	srcRhos_array::Vector{S}=[0.0],
	srcRadii_array::Vector{S}=[0.0],
	srcLengths_array::Vector{S}=[0.0],
	ispoint::Bool=true
	)::Vector{String} 	where S <: Real
```

**[`batch(::Vector{Detector}, ::Vector{Real},::Vector{Real},::Vector{Real},::Vector{Real},::Bool)`](@ref)** と同様ですが、`getDetectors`を適用した後に`detector_info_array`内の検出器の`幾何学的効率`のバッチ計算を提供します。結果を保存する各検出器のファイルの**`CSV`**へのパスのリストを返します。
