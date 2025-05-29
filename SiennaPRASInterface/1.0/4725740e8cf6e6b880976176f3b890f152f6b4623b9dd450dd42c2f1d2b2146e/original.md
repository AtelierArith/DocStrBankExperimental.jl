```julia
set_device_model!(
    template::SiennaPRASInterface.RATemplate,
    _::Type{D<:PowerSystems.Device},
    _::Type{B<:SiennaPRASInterface.AbstractRAFormulation}
) -> Vector{SiennaPRASInterface.DeviceRAModel}

```

# Arguments

  * `template::RATemplate`: Template to add device model to
  * `::Type{D}`: Device type
  * `::Type{B}`: Formulation type

Adds a device model to a RATemplate by passing the type to a constructor.
