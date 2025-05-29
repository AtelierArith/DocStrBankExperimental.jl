ClusterManager for a Slurm allocation

Represents the resources available within a slurm allocation created by salloc/sbatch.
The environment variables `SLURM_JOB_ID` or `SLURM_JOBID` and `SLURM_NTASKS` must be defined to construct this object.
