```julia
Data(
    grid,
    numberOfCarriers;
    contactVoltageFunction,
    generationData,
    statfunctions
) -> ChargeTransport.Data{ChargeTransport.StandardFuncSet, T, Vector{Float64}} where T<:Function

```

グリッドとキャリア数のみを引数として受け取るDataの簡略化されたコンストラクタ。ここでは、物理的なパラメータを含むすべての必要な情報と、いくつかの数値情報が配置されています。
