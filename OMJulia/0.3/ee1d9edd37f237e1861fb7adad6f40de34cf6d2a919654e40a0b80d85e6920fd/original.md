```
sensitivity(omc::OMCSession, Vp, Vv, Ve=[1e-2])
```

Method for computing numeric sensitivity of OpenModelica object.

## Arguments

  * `omc::OMCSession`:                OpenModelica compiler session.
  * `Vp::Array{<:AbstractString, 1}`:   Modelica Parameter names.
  * `Vv::Array{<:AbstractString, 1}`:   Modelica Variable names.
  * `Ve::Array{Float64, 1}`:          Excitations of parameters; defaults to scalar 1e-2

## Return

  * `VSname::Vector{Vector{String}}`:             Vector of sensitivity names
  * `VSarray::Vector{Vector{Vector{Float64}}}`:   Vector of sensitivies: vector of elements per parameter

Each element containing time series per variable
