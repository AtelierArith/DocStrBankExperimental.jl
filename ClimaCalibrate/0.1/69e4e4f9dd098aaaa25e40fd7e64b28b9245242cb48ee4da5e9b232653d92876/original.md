```
calibrate(backend, ekp::EnsembleKalmanProcess, ensemble_size, n_iterations, prior, output_dir)
calibrate(backend, ensemble_size, n_iterations, observations, noise, prior, output_dir; ekp_kwargs...)
```

Run a full calibration on the given backend.

If the EKP struct is not given, it will be constructed upon initialization.  While EKP keyword arguments are passed through to the EKP constructor, if using many keywords it is recommended to construct the EKP object and pass it into `calibrate`.

Available Backends: WorkerBackend, CaltechHPCBackend, ClimaGPUBackend, DerechoBackend, JuliaBackend

Derecho, ClimaGPU, and CaltechHPC backends are designed to run on a specific high-performance computing cluster. WorkerBackend uses Distributed.jl to run the forward model on workers.

## Keyword Arguments for HPC backends

  * `model_interface: Path to the model interface file.
  * `hpc_kwargs`: Dictionary of resource arguments for HPC clusters, passed to the job scheduler.
  * `verbose::Bool`: Enable verbose logging.
  * Any keyword arguments for the EnsembleKalmanProcess constructor, such as `scheduler`
