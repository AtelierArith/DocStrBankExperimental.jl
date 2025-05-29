```
RecordAction
```

A `RecordAction` is a small functor to record values. The usual call is given by

```
(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, i) -> s
```

that performs the record for the current problem and solver combination, and where `i` is the current iteration.

By convention `i=0` is interpreted as "For Initialization only," so only initialize internal values, but not trigger any record, that the record is called from within [`stop_solver!`](@ref) which returns true afterwards.

Any negative value is interpreted as a “reset”, and should hence delete all stored recordings, for example when reusing a `RecordAction`. The start of a solver calls the `:Iteration` and `:Stop` dictionary entries with `-1`, to reset those recordings.

By default any `RecordAction` is assumed to record its values in a field `recorded_values`, an `Vector` of recorded values. See [`get_record`](@ref get_record(r::RecordAction))`(ra)`.
