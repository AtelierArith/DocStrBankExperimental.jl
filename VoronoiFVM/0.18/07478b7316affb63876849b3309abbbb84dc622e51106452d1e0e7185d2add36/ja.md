```julia
testfunction(
    factory::VoronoiFVM.TestFunctionFactory,
    bc0,
    bc1
) -> Any

```

bc0の境界領域に対してディリクレゼロ境界条件を持ち、bc1の境界領域に対してディリクレ一境界条件を持つtestfunctionを作成します。
