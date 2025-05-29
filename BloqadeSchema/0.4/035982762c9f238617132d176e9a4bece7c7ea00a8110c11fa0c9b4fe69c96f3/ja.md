```
to_schema_no_validation(lattice::Union{Vector,Lattice};
    ϕ::Maybe{PiecewiseConstantWaveform}=nothing,
    Ω::Maybe{PiecewiseLinearWaveform}=nothing,
    Δ::Maybe{PiecewiseLinearWaveform}=nothing,
    δ::Maybe{PiecewiseLinearWaveform}=nothing,
    Δi::Maybe{Vector{Number}}=nothing, 
    nshots::Int,
    device_capabilities::DeviceCapabilities=get_device_capabilities())
to_schema_no_validation(lattice::Union{Vector,Lattice},
    ϕ::Maybe{PiecewiseConstantWaveform},
    Ω::Maybe{PiecewiseLinearWaveform},
    Δ::Maybe{PiecewiseLinearWaveform},
    δ::Maybe{PiecewiseLinearWaveform},
    Δi::Maybe{Vector{Number}}, 
    params::SchemaTranslationParams)
```

`lattice`、`ϕ`、`Δ`、`δ`、および`Δi`を、提供された値が機械で実行可能であること（デバイスの能力の制約内に収まること）を確認せずに、`QuEraTaskSpecification`インスタンスに変換します。

`params`がまだ提供されていない場合、`nshots::Int`と`device_capabilities`から自動的に構築されます。

[`to_schema`](@ref)も参照してください。
