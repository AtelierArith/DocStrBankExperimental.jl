```julia
set_service_model!(
    template::PowerSimulations.ProblemTemplate,
    service_type::Type{<:PowerSystems.Service},
    formulation::Type{<:PowerSimulations.AbstractServiceFormulation}
)

```

テンプレート内でServiceModelインスタンスを使用してサービスモデルを設定します。
