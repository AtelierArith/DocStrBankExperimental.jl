```
mutable struct Inputs{T<:Phases} <: AbstractInputs
    edges::Array{Tuple, 1}
    linecodes::Array{String, 1}
    linelengths::Array{Float64, 1}
    busses::Array{String}
    phases::Vector{Vector}
    substation_bus::String
    Pload::Dict{String, Any}
    Qload::Dict{String, Any}
    Sbase::Real
    Vbase::Real
    Ibase::Real
    Zdict::Dict{String, Dict{String, Any}}
    v0::Real
    v_lolim::Real
    v_uplim::Real
    Zbase::Real
    Ntimesteps::Int
    pf::Float64
    Nnodes::Int
    P_up_bound::Float64
    Q_up_bound::Float64
    P_lo_bound::Float64
    Q_lo_bound::Float64
    Isquared_up_bounds::Dict{String, <:Real}
    phases_into_bus::Dict{String, Vector{Int}}
    relaxed::Bool
    edge_keys::Vector{String}
    regulators::Dict
    shunt_susceptance::Dict
end
```

Inputs

  * `edges` Vector{Tuple} e.g. `[("0", "1"), ("1", "2")]`
  * `linecodes` vector of string keys for the Zdict (impedance values for lines). When using an OpenDSS model a `linecode` is the `name` in `New linecode.name`
  * `linelengths` vector of floats to scale impedance values
  * `busses` vector of bus names
  * `phases` vector of vectors with ints for the line phases (e.g. `[[1,2,3], [1,3], ...]`)
  * `Pload` dict with `busses` for keys and uncontrolled real power loads (positive is load) by phase and time
  * `Qload` dict with `busses` for keys and uncontrolled reactive power loads (positive is load) by phase and time
  * `Sbase` base apparent power for network, typ. feeder capacity. Used to normalize all powers in model
  * `Vbase` base voltage for network, used to determine `Zbase = Vbase^2 / Sbase`
  * `Ibase` = `Sbase / (Vbase * sqrt(3))`
  * `Zdict` dict with `linecodes` for keys and subdicts with "xmatrix" and "zmatrix" keys with per unit length values. Values are divided by `Zbase` and multiplied by linelength in mathematical model.
  * `v0` slack bus reference voltage

TODO Zdict example

TODO test against simple model to make sure scaling is done right

!!! note
    The `edges`, `linecodes`, `phases`, `edge_keys`, and `linelengths` are in mutual order (i.e. the i-th value in each list corresponds to the same line)

