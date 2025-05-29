```
mpi_isroot()
```

Helper function that returns a bool indicating if a process is the MPI root process. It can be safely used even for multithreading simulations, as it is always `true` if the package is started in a normal Julia environment which is not started by MPI.
