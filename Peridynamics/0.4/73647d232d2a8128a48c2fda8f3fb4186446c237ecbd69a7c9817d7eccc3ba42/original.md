```
enable_mpi_timers!()
```

Helper function to enable timers defined with the `TimerOutputs` for simulations with the MPI backend. The results of the timers then will be exported into the specified path of a [`Job`](@ref). By default, not timers will be used with MPI simulations. It can be safely used with multithreading.

See also [`disable_mpi_timers!`](@ref).
