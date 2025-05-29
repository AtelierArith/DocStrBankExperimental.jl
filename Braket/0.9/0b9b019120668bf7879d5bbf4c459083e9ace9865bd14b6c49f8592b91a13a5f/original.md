```
LocalSimulator(backend::Union{String, AbstractBraketSimulator})
```

A quantum simulator which runs *locally* rather than sending the circuit(s) to the cloud to be executed on-demand. A `LocalSimulator` must be created with a backend – either a handle, in the form of a `String`, which uniquely identifies a simulator backend registered in [`_simulator_devices`](@ref Braket._simulator_devices), or an already instantiated simulator object.

`LocalSimulator`s should implement their own method for [`simulate`](@ref) if needed. They can process single tasks or task batches.
