```
to_json_no_validation(lattice::Union{Vector,Lattice};
    ϕ::Maybe{PiecewiseConstantWaveform}=nothing,
    Ω::Maybe{PiecewiseLinearWaveform}=nothing,
    Δ::Maybe{PiecewiseLinearWaveform}=nothing,
    δ::Maybe{PiecewiseLinearWaveform}=nothing,
    Δi::Maybe{Vector{Number}}=nothing,kw...)
```

`lattice`、`ϕ`、`Δ`、`δ`、および `Δi` を、提供された値がマシン上で実行可能であること（デバイスの能力の制約内に収まること）を確認せずに、`QuEraTaskSpecification` インスタンスの JSON 表現に変換します。

[`to_json`](@ref) も参照してください。
