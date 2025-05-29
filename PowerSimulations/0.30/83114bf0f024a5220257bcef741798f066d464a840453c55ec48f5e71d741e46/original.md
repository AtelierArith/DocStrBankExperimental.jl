```julia
set_device_model!(
    template::PowerSimulations.ProblemTemplate,
    component_type::Type{<:PowerSystems.Device},
    formulation::Type{<:PowerSimulations.AbstractDeviceFormulation}
)

```

Sets the device model in a template using the component type and formulation. Builds a default DeviceModel
