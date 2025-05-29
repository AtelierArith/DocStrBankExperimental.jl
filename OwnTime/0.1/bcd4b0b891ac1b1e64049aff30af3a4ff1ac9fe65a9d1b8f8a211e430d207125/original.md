```
totaltime([stacktraces]; stackframe_filter, warn_on_full_buffer=true)
```

Count the time spent on each `StackFrame` *including* its sub-calls.

If supplied, `stackframe_filter` should be a function that accepts a single `StackFrame` and returns `true` if it should be included in the counts.

More advance filtering my by done by preprocessing the `StackTrace`s from `OwnTime.stacktraces()` and then passing those `StackTrace`s to this function.

See also: [`OwnTime.stacktraces`](@ref) [`StackTraces.StackFrame`](@ref)
