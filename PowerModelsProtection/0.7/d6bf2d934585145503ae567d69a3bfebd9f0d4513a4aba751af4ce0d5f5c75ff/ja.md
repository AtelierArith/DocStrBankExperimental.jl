```
create_fault(type::String, bus::String, connections::Vector{Int}, resistance::Real, phase_resistance::Real)::Dict{String,Any}
```

与えられた`type`の故障、すなわち「3pq」、「llg」のいずれか、故障が発生している`bus`、故障が適用される`connections`、位相と接地間の`resistance`、および位相間の`phase_resistance`に基づいて故障辞書を作成します。
