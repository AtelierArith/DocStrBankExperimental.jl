```julia
run_parallel_simulation(
    build_function,
    execute_function;
    script,
    output_dir,
    name,
    num_steps,
    period,
    num_overlap_steps,
    num_parallel_processes,
    exeflags,
    force
)

```

Run a partitioned simulation in parallel on a local computer.

# Arguments

  * `build_function`: Function reference that returns a built Simulation.
  * `execute_function`: Function reference that executes a Simulation.
  * `script::AbstractString`: Path to script that includes $build_function$ and $execute_function$.
  * `output_dir::AbstractString`: Path for simulation outputs
  * `name::AbstractString`: Simulation name
  * `num_steps::Integer`: Total number of steps in the simulation
  * `period::Integer`: Number of steps in each simulation partition
  * `num_overlap_steps::Integer`: Number of steps that each partition overlaps with the previous partition
  * `num_parallel_processes`: Number of partitions to run in parallel. If nothing, use the number of cores.
  * `exeflags`: Path to Julia project. Forwarded to Distributed.addprocs.
  * `force`: Overwrite the output directory if it already exists.
