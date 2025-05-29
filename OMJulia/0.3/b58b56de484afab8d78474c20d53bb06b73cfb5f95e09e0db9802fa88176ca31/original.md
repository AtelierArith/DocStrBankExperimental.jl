```
getSimulationOptions(omc, name=nothing)
```

Return SimulationOption variables parsed from xml file.

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:     Names of parameters to read from xml file.                                                                      If nothing is provided read all parameters.
