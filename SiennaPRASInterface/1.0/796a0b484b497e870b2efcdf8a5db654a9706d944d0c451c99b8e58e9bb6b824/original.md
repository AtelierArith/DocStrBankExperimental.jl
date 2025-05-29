```julia
set_device_model!(
    template::SiennaPRASInterface.RATemplate,
    device_model::SiennaPRASInterface.DeviceRAModel{D}
) -> Vector{SiennaPRASInterface.DeviceRAModel}

```

# Arguments

  * `template::RATemplate`: Template to add device model to
  * `device_model::DeviceRAModel{D}`: Device model to add

Add a device model to a RATemplate. If an existing model already applies to the given device type, then a warning is issued. However, newer models will take precedence.
