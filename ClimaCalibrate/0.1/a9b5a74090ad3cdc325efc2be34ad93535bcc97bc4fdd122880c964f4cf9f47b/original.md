```
model_run(backend, iter, member, output_dir, experiment_dir; model_interface, verbose, hpc_kwargs)
```

Construct and execute a command to run a single forward model on a given job scheduler.

Dispatches on `backend` to run [`slurm_model_run`](@ref) or [`pbs_model_run`](@ref).

Arguments:

  * iter: Iteration number
  * member: Member number
  * output_dir: Calibration experiment output directory
  * project_dir: Directory containing the experiment's Project.toml
  * model_interface: Model interface file
  * module*load*str: Commands which load the necessary modules
  * hpc_kwargs: Dictionary containing the resources for the job. Easily generated using [`kwargs`](@ref).
