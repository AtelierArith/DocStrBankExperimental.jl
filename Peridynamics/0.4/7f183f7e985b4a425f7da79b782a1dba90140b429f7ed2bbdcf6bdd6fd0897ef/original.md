```
disable_mpi_timers!()
```

Helper function to disable timers defined with the `TimerOutputs` for simulations with the MPI backend. It is mainly used to reset the behaviour after a call of [`enable_mpi_timers!`](@ref). It can be safely used with multithreading.
