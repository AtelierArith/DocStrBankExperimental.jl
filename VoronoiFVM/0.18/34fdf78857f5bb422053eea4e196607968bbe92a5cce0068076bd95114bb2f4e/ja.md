```julia
unknowns(
    edge::VoronoiFVM.AbstractEdge,
    u::AbstractArray{Tv, 1},
    i
) -> VoronoiFVM.VectorUnknowns

```

エッジ上のベクトル未知数を構築します。
