```
RecordSubsolver <: RecordAction
```

Record the current sub solvers recording, by calling [`get_record`](@ref) on the sub state with

# Fields

  * `records`: an array to store the recorded values
  * `symbols`: arguments for [`get_record`](@ref). Defaults to just one symbol `:Iteration`, but could be set to also record the `:Stop` action.

# Constructor

```
RecordSubsolver(; record=[:Iteration,], record_type=eltype([]))
```
