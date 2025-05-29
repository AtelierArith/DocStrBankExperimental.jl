```
getInputs(omc, name=nothing)
```

Return output variables parsed from xml file. If output variables have no start value the returned value is `"None"`.

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:  Names of output variables to read from xml file.                                                                       If nothing is provided read all output variables.
