```julia
set_service_model!(
    template::PowerSimulations.ProblemTemplate,
    service_type::Type{<:PowerSystems.Service},
    formulation::Type{<:PowerSimulations.AbstractServiceFormulation}
)

```

Sets the service model in a template using a ServiceModel instance.
