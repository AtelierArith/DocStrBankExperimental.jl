```
setSimulationOptions(omc, name)
```

Set simulation option values like `stopTime` or `stepSize`.

## Arguments

  * `omc::OMCSession`: OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}}`:  String "Name=value" or                                                              vector of strings ["Name1=value1","Name2=value2","Name3=value3"])
