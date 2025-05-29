```
get_record(s::AbstractManoptSolverState, [,symbol=:Iteration])
get_record(s::RecordSolverState, [,symbol=:Iteration])
```

return the recorded values from within the [`RecordSolverState`](@ref) `s` that where recorded with respect to the `Symbol symbol` as an `Array`. The default refers to any recordings during an `:Iteration`.

When called with arbitrary [`AbstractManoptSolverState`](@ref), this method looks for the [`RecordSolverState`](@ref) decorator and calls `get_record` on the decorator.
