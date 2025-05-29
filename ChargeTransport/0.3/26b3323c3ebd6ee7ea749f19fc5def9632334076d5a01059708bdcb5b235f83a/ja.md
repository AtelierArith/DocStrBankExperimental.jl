```julia
etaFunction(
    sol,
    ireg::Int64,
    ctsys,
    icc::Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}
) -> Any

```

与えられた内部領域における与えられた解に対する統計関数の引数。
