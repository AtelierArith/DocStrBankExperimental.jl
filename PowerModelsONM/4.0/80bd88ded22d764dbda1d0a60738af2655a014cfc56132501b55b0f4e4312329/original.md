```
get_timestep_fault_currents(
    fault_studies_results::Dict{String,<:Any},
    faults::Dict{String,<:Any},
    network::Dict{String,<:Any};
    ret_protection_only::Bool=false
)::Vector{Dict{String,Any}}
```

Gets information about the results of fault studies at each timestep, including:

  * information about the fault, such as

      * the admittance (`"conductance (S)"` and `"susceptance (S)"`),
      * the bus at which the fault is applied
      * the type of fault (3p, 3pg, llg, ll, lg), and
      * to which connections the fault applies
  * information about the state at the network's protection, including

      * the fault current `|I| (A)`
      * the zero-sequence fault current `|I0| (A)`
      * the positive-sequence fault current `|I1| (A)`
      * the negative-sequence fault current `|I2| (A)`
      * the bus voltage from the from-side of the switch `|V| (V)`
      * the bus voltage angle from the from-side of the switch `phi (deg)`

`ret_protection_only==false` indicates that currents and voltages should be returned for all lines where switch=y, and if `true`, should only return switches for which a protection device is defined (recloser, relay, fuse)
