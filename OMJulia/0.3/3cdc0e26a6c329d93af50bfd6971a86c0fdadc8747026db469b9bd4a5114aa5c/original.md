```
getSolutions(omc::OMCSession, name=nothing; resultfile=nothing)
```

Read result file and return simulation results

## Arguments

  * `omc::OMCSession`:        OpenModelica compiler session.
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:  Names of variables to read from result file.                                                                       If nothing is provided read all variables.

## Keyword Arguments

  * `resultfile::Union{AbstractString, Nothing}`:     Path to result file. If nothing is provided use saved result file.
