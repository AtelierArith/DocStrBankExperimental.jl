```
get_record(r::RecordGroup)
```

return an array of tuples, where each tuple is a recorded set per iteration or record call.

```
get_record(r::RecordGruop, k::Int)
```

return an array of values corresponding to the `i`th entry in this record group

```
get_record(r::RecordGruop, s::Symbol)
```

return an array of recorded values with respect to the `s`, see [`RecordGroup`](@ref).

```
get_record(r::RecordGroup, s1::Symbol, s2::Symbol,...)
```

return an array of tuples, where each tuple is a recorded set corresponding to the symbols `s1, s2,...` per iteration / record call.
