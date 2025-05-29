```
getindex(r::RecordGroup, s::Symbol)
r[s]
getindex(r::RecordGroup, sT::NTuple{N,Symbol})
r[sT]
getindex(r::RecordGroup, i)
r[i]
```

`s`、タプル`sT`のシンボル、またはインデックス`i`に関して記録された値の配列を返します。詳細については、[`get_record`](@ref get_record(r::RecordGroup))を参照してください。
