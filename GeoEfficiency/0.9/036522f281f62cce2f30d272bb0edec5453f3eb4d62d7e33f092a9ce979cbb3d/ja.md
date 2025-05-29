```
batch( 
	detectors_array::Vector{<: Detector},
    srcHeights_array::Vector{S},
    srcRhos_array::Vector{S}=[0.0],
    srcRadii_array::Vector{S}=[0.0],
    srcLengths_array::Vector{S}=[0.0],
	ispoint::Bool=true
	)::Vector{String} where S <: Real
```

**[`batch(::Detector, ::Vector{Real},::Vector{Real},::Vector{Real},::Vector{Real},::Bool)`](@ref)** と同様ですが、検出器のリスト `detectors_array` を受け入れます。結果を保存する各検出器のファイルの **`CSV`** へのパスのリストを返します。
