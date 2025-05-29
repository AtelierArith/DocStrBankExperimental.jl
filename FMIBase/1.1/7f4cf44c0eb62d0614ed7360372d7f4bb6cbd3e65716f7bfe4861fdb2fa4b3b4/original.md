```
getDeclaredType(md::fmi2ModelDescription, mv::fmi2ScalarVariable)
```

Returns the `fmi2SimpleType` of the corresponding model variable `mv` as defined in `md.typeDefinitions`. If `mv` does not have a declared type, return `nothing`. If `mv` has a declared type, but it is not found, issue a warning and return `nothing`.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.
  * `mv::fmi2ScalarVariable`: The “ModelVariables” element consists of an ordered set of “ScalarVariable” elements. A “ScalarVariable” represents a variable of primitive type, like a real or integer variable.

# Source

  * FMISpec2.0.3 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.3: 2.2.7  Definition of Model Variables (ModelVariables)
