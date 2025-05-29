```
SlurmManager(ntasks=get(ENV, "SLURM_NTASKS", 1))
```

The ClusterManager for Slurm clusters, taking in the number of tasks to request with `srun`.

To execute the `srun` command, run `addprocs(SlurmManager(ntasks))`

Keyword arguments can be passed to `srun`: `addprocs(SlurmManager(ntasks), gpus_per_task=1)`

By default the workers will inherit the running Julia environment.

To run a calibration, call `calibrate(WorkerBackend, ...)`

To run functions on a worker, call `remotecall(func, worker_id, args...)`
