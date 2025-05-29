```julia
set_service_model!(
    template::PowerSimulations.ProblemTemplate,
    service_name::String,
    service_type::Type{<:PowerSystems.Service},
    formulation::Type{<:PowerSimulations.AbstractServiceFormulation}
)

```

Sets the service model in a template using a name and the service type and formulation. Builds a default ServiceModel with use*service*name set to true.
