```
struct SchemaTranslationParams
```

Used to specify number of times a Hamiltonian should be executed and the capabilities of the machine the Hamiltonian will be executed on as an argument to functions that convert Hamiltonians to other formats.

See also [`to_schema`](@ref), [`to_dict`](@ref), [`to_json`](@ref)

# Fields

  * `nshots::Int = 1`:  The number of times a Hamiltonian should be executed
  * `device_capabilities::DeviceCapabilities = get_device_capabilities()`: capabilities of the machine the Hamiltonian will be executed on
