```
getQuantities(omc, name=nothing)
```

Return list of all variables parsed from xml file.

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`: Names of variables to read from xml file.                                                                      If nothing is provided read all variables.

See also [`showQuantities`](@ref).
