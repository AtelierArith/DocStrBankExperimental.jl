```
add_fault!(data::Dict{String,Any}, name::String, type::String, bus::String, connections::Vector{Int}, resistance::Real)
```

指定された`type`の故障（"3pq"、"llg"のいずれか）、故障が発生している`bus`、故障が適用される`connections`、位相と接地間の`resistance`、位相間の`phase_resistance`を考慮して、故障辞書を作成し、それを`data["fault"]`の下の`"name"`に追加します。
