```julia
set_service_model!(
    template::PowerSimulations.ProblemTemplate,
    service_name::String,
    service_type::Type{<:PowerSystems.Service},
    formulation::Type{<:PowerSimulations.AbstractServiceFormulation}
)

```

テンプレート内で名前とサービスの種類および定式化を使用してサービスモデルを設定します。デフォルトのServiceModelを構築し、use*service*nameをtrueに設定します。
