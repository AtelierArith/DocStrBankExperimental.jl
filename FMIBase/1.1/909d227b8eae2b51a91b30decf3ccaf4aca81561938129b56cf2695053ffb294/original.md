```
stringToValueReference(obj, names)
```

Finds the value reference for a given `name`.

# Arguments

  * `obj ∈ (fmi2ModelDescription, fmi3ModelDescription, FMU2, FMU3)` the FMI object
  * `names ∈ (String, AbstractVector{String})` the value refernce name or multiple names

# Return

Returns a single or an array of `fmi2ValueReferences` (FMI2) or `fmi3ValueReferences` (FMI3) corresponding to the variable name(s).
