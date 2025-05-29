```
MPIWorkerManager([nprocs])
```

A [`ClusterManager`](https://docs.julialang.org/en/v1/stdlib/Distributed/#Distributed.ClusterManager) using the MPI.jl launcher [`mpiexec`](https://juliaparallel.github.io/MPI.jl/stable/environment/#MPI.mpiexec).

The workers will all belong to an MPI session, and can communicate using MPI operations. Note that unlike `MPIManager`, the MPI session will not be initialized, so the workers will need to `MPI.Init()`.

The master process (pid 1) is *not* part of the session, and will communicate with the workers via TCP/IP.

# Usage

```
using Distributed, MPIClusterManager

mgr = MPIWorkerManager(4) # launch 4 MPI workers
mgr = MPIWorkerManager() # launch the default number of MPI workers (determined by `mpiexec`)

addprocs(mgr; kwoptions...)
```

The following `kwoptions` are supported:

  * `dir`: working directory on the workers.
  * `mpiexec`: MPI launcher executable (default: use the launcher from MPI.jl)
  * `mpiflags`: additional flags  to pass to `mpiexec`
  * `exename`: Julia executable on the workers.
  * `exeflags`: additional flags to pass to the Julia executable.
  * `threadlevel`: the threading level to initialize MPI. See

[`MPI.Init()`](https://juliaparallel.github.io/MPI.jl/stable/environment/#MPI.Init)  for details.

  * `topology`: how the workers connect to each other.
  * `enable_threaded_blas`: Whether the workers should use threaded BLAS.
  * `master_tcp_interface`: Server interface to listen on. This allows direct connection from other hosts on same network as specified interface (otherwise, only connections from `localhost` are allowed).
