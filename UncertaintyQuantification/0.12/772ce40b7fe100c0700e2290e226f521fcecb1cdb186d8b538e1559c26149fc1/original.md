```
SlurmInterface(options::Dict{String,String}, throttle::Integer, btachsize::Integer, extras::Vector{String})
```

When `SlurmInterface` is passed to an `ExternalModel`, model evaluations are executed using slurm job arrays. This allows for heavier simulations or workflows to be sampled, without relying on Julia's native parallelism. `SlurmInterface` automatically generates a slurm job array script, and Julia waits for this job to finish before extracting results.

When using `SlurmInterface`, you no longer need to load workers into Julia with `addprocs(N)`, and the requested nodes / tasks those required by individual model evaluations. Use `extras` to specify anything that must be preloaded for your models to be executed (for example loading modules).

The `throttle` specifies the number of simulations in the job array which are run concurrently. I.e., if you perform `MonteCarlo` simulation with `N=1000` samples, with `throttle=200`, it will run 1000 simulations in total, but only 200 at the same time. Your HPC scheduler (and admin) may be unhappy if you request too many concurrent jobs. If left empty, you scheduler's default throttle will be used. In the case that your HPC machine limits the size of submitted job arrays, you can split the submissions into smaller "batches". Specify "batchsize" to the maximum size of a job array. This does not change the total number of runs.

# parameters

```
options   : A dictionary of SBATCH options to add to the slurm script
throttle  : the number of jobs to be run at the same time
batchsize : maximum size of the slurm array, use when HPC limits the number of jobs in arrays
extras    : instructions to be executed before the model is run, e.g. activating a python environment or loading modules
```

# Examples

```jldoctest
julia> slurm = SlurmInterface(Dict("account" => "HPC_account_1", "partition" => "CPU_partition"), extras = ["load python3"])
SlurmInterface(Dict("account" => "HPC_account_1", "partition" => "CPU_partition"), 0, 0, ["load python3"])
```
