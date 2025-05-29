```
IntegrateOverConfidenceRegion(DM::AbstractDataModel, Domain::HyperCube, Confnum::Real, F::Function; N::Int=Int(1e5), WE::Bool=true, kwargs...)
```

関数 `F` を `Domain` とレベル `Confnum` の信頼領域の交差部分で積分します。
