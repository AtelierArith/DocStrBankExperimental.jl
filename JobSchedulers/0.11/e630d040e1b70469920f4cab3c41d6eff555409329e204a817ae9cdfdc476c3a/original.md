```
close_in_future(io::IO, job::Job; kwargs...)
close_in_future(io::IO, jobs::Vector{Job}; kwargs...)
```

Close `io` after `job` is in PAST status (either DONE/FAILED/CANCELLED). It is userful if jobs uses `::IO` as `stdout` or `stderr`, because the program will not close `::IO` manually!

`kwargs...` include keyword arguments of `Job(::BaseAbstractCmd, ...)` and `run(::Program, ...)`.
