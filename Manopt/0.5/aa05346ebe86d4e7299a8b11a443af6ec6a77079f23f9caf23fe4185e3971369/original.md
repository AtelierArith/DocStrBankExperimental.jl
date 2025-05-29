```
get_index(rs::RecordSolverState, s::Symbol)
ro[s]
```

Get the recorded values for recorded type `s`, see [`get_record`](@ref) for details.

```
get_index(rs::RecordSolverState, s::Symbol, i...)
ro[s, i...]
```

Access the recording type of type `s` and call its [`RecordAction`](@ref) with `[i...]`.
