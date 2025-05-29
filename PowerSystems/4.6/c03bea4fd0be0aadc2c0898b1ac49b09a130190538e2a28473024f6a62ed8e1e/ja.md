```julia
get_contributing_device_mapping(
    sys::PowerSystems.System
) -> Dict{@NamedTuple{type::DataType, name::String}, PowerSystems.ServiceContributingDevices}

```

ServiceContributingDevicesMappingのインスタンスを返します。
