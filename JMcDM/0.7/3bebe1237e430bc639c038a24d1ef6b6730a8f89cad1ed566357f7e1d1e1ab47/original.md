```
mcdm(setting, method = TopsisMethod())

Perform selected method for a given decision matrix, weight vector, and function list.
```

# Arguments:

  * `setting::MCDMSetting`: MCDMSetting object that holds the decision matrix, weight vector, and functions.
  * `method::MCDMMethod`: Preferred MCDMMethod. The default is TopsisMethod().

# Description

The method is one of the subtypes of MCDMMethod type. See examples.

# Output

  * `::MCDMResult`: An object derived from subtypes of MCDMResult type.

# Examples

```julia-repl
julia> # mcdm() for Topsis:
julia> # mcdm(setting, TopsisMethod())

julia> # mcdm() for Saw:
julia> # mcdm(setting, SawMethod())

julia> # mcdm() with optional parameters:
julia> # mcdm(setting, GreyMethod(0.6))
```
