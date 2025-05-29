```
getContinuous(omc, name=nothing)
```

Return continuous variables parsed from xml file.

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:  Names of continuous variables to read from xml file.                                                                       If nothing is provided read all continuous variables.
