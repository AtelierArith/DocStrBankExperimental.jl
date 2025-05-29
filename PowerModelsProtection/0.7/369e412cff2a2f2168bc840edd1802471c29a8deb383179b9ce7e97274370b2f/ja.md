```
create_fault(type::String, bus::String, connections::Vector{Int}, resistance::Real, phase_resistance::Real)::Dict{String,Any}
```

与えられた`type`の故障、すなわち「3p」、「ll」、「lg」のいずれか、故障が発生している`bus`、故障が適用される`connections`、および「lg」の場合の相と接地間の`resistance`、または相と相間の`resistance`を考慮して、故障辞書を作成します。
