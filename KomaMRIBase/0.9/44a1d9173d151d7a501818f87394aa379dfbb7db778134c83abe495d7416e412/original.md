```
heartbeat = HeartBeat(circumferential_strain, radial_strain, longitudinal_strain)
```

HeartBeat struct. It produces a heartbeat-like motion, characterised by three types of strain: circumferential, radial and longitudinal

# Arguments

  * `circumferential_strain`: (`::Real`) contraction parameter
  * `radial_strain`: (`::Real`) contraction parameter
  * `longitudinal_strain`: (`::Real`) contraction parameter

# Returns

  * `heartbeat`: (`::HeartBeat`) HeartBeat struct

# Examples

```julia-repl
julia> heartbeat = HeartBeat(circumferential_strain=-0.3, radial_strain=-0.2, longitudinal_strain=0.0)
```
