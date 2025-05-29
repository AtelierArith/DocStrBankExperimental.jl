```julia
set_device_model!(
    template::PowerSimulations.ProblemTemplate,
    component_type::Type{<:PowerSystems.Device},
    formulation::Type{<:PowerSimulations.AbstractDeviceFormulation}
)

```

テンプレート内のデバイスモデルをコンポーネントタイプと定式化を使用して設定します。デフォルトのDeviceModelを構築します。
