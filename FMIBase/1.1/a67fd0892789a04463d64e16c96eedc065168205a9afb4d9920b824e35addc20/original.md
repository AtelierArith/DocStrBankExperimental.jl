```
getInitial(mv::fmi2ScalarVariable)
```

Returns the `inital` entry of the corresponding model variable.

# Arguments

  * `fmi2GetStartValue(mv::fmi2ScalarVariable)`: The “ModelVariables” element consists of an ordered set of “ScalarVariable” elements. A “ScalarVariable” represents a variable of primitive type, like a real or integer variable.

# Returns

  * `mv.Real.unit`: Returns the `inital` entry of the corresponding ScalarVariable representing a variable of the primitive type Real. Otherwise `nothing` is returned.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2: 2.2.7  Definition of Model Variables (ModelVariables)
