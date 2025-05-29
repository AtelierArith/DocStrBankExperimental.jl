```
setParameters(omc, name; verbose=true)
```

Set parameter values for parameter variables defined by users

## Arguments

  * `omc::OMCSession`: OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}}`:  String "Name=value" or                                                              vector of strings ["Name1=value1","Name2=value2","Name3=value3"])

## Keyword Arguments

  * `verbose::Bool`:     Display additional info if setParameters failed.
