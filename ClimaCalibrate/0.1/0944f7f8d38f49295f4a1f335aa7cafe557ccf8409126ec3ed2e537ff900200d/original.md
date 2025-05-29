```
PBSManager(ntasks)
```

The ClusterManager for PBS/Torque clusters, taking in the number of tasks to request with `qsub`.

To execute the `qsub` command, run `addprocs(PBSManager(ntasks))`.  Unlike the [`SlurmManager`](@ref), this will not nest scheduled jobs, but will acquire new resources.

Keyword arguments can be passed to `qsub`: `addprocs(PBSManager(ntasks), nodes=2)`

By default, the workers will inherit the running Julia environment.

To run a calibration, call `calibrate(WorkerBackend, ...)`

To run functions on a worker, call `remotecall(func, worker_id, args...)`
