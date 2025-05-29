```
add_fault!(data::Dict{String,Any}, name::String, type::String, bus::String, connections::Vector{Int}, resistance::Real, phase_resistance::Real)
```

指定された`type`の故障（"3p"、"ll"、"lg"のいずれか）、故障が発生している`bus`、故障が適用される`connections`、"lg"の場合の位相と接地間の`resistance`、または位相間の`resistance`を考慮して、故障辞書を作成し、`data["fault"]`の`"name"`の下に追加します。
