```
constrain(udata::Vector{<:AbstractUncertainValue}, 
	s::SamplingConstraint) -> ConstrainedUncertainValueDataset
```

不確実な値のベクトルを返します。これは、`udata`内の各不確実な値に制約`s`を適用することによって得られます。
