```
AbstractCircuitParameters
```

Circuit parameters should be stored in a subtype `T <: AbstractCircuitParameters`.

Then add a method to [`get_circuit`](@ref) that generates a circuit according to these parameters. Such a circuit should either be a [`Circuit`](@ref) object, or a subtype `T <: AbstractCircuit`.

# Necessary fields

  * `params::Dict{Symbol, Any}`: Dictionary of the circuit parameters, which should in particular include a `layer_time_dict` field, which is a dictionary of the times taken to implement the different types of layers in the circuit, including the time for measurement and reset.
  * `circuit_name::String`: Name of the circuit, which should implicitly describe parameter settings.
