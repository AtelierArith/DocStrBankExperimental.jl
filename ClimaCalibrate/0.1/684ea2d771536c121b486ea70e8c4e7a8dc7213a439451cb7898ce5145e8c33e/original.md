```
wait_for_jobs(jobids, output_dir, iter, experiment_dir, model_interface, module_load_str, model_run_func; verbose, hpc_kwargs, reruns=1)
```

Wait for a set of jobs to complete. If a job fails, it will be rerun up to `reruns` times.

This function monitors the status of multiple jobs and handles failures by rerunning the failed jobs up to the specified number of `reruns`. It logs errors and job completion status, ensuring all jobs are completed before proceeding.

Arguments:

  * `jobids`: Vector of job IDs.
  * `output_dir`: Directory for output.
  * `iter`: Iteration number.
  * `experiment_dir`: Directory for the experiment.
  * `model_interface`: Interface to the model.
  * `module_load_str`: Commands to load necessary modules.
  * `model_run_func`: Function to run the model.
  * `verbose`: Print detailed logs if true.
  * `hpc_kwargs`: HPC job parameters.
  * `reruns`: Number of times to rerun failed jobs.
