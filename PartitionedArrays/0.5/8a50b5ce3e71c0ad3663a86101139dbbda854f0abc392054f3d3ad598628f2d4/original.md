```
tic!(t::PTimer;barrier=false)
```

Reset the timer `t` to start measuring the time in a section.   If `barrier==true`, all process will be synchronized before  resetting the timer if using a distributed back-end. For MPI, this will result in a call to `MPI.Barrier`.
