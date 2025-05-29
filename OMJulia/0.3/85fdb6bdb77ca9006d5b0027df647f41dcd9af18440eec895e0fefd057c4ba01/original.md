```
getInputs(omc, name=nothing)
```

Return input variables parsed from xml file. If input variables have no start value the returned value is `"None"`.

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:     Names of input variables to read from xml file.                                                                      If nothing is provided read all input variables.
