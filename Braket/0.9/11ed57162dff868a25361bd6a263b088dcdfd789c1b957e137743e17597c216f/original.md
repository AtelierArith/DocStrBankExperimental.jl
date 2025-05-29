```
ir(c::Circuit; serialization_properties::SerializationProperties=OpenQASMSerializationProperties())
```

Convert a [`Circuit`](@ref) into IR that can be consumed by the Amazon Braket service, whether local simulators, on-demand simulators, or QPUs. The IR format to convert to by default is controlled by the global variable [`IRType`](@ref), which can be modified. Currently `:JAQCD` and `:OpenQASM` are supported for `Circuit`s. If writing to `OpenQASM` IR, optional [`OpenQASMSerializationProperties`](@ref) may be specified.
