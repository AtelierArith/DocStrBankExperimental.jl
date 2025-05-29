```
getInputValueReferencesAndNames(md::fmi2ModelDescription)
```

Returns a dict with (vrs, names of inputs).

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.
  * `fmu::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.

# Returns

  * `dict::Dict{fmi2ValueReference, Array{String}}`: Returns a dictionary that constructs a hash table with keys of type fmi2ValueReference and values of type Array{String}. So returns a dict with (vrs, names of inputs)
