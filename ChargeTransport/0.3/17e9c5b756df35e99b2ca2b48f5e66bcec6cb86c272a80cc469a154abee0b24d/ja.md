```julia
get_density(
    sol,
    ireg::Int64,
    ctsys,
    icc::Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}
) -> Any

```

与えられたポテンシャルに対して、均一なパラメータセットに対応する与えられた内部領域の密度を計算します。
