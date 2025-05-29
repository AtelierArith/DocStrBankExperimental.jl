```
prepareValueReference(obj, vrs)
```

where: 

obj ∈ (fmi2ModelDescription, fmi3ModelDescription, FMU2, FMU3, FMU2Component, FMU3Instance) vrs ∈ (fmi2ValueReference, AbstractVector{fmi2ValueReference},         fmi3ValueReference, AbstractVector{fmi3ValueReference},         String, AbstractVector{String},         Integer, AbstractVector{Integer},        :states, :derivatives, :inputs, :outputs, :all, :none,        Nothing)

Receives one or an array of value references in an arbitrary format (see fmi2ValueReferenceFormat) and converts it into an Array{fmi2ValueReference} (if not already).
