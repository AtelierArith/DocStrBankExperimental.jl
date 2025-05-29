```
isrunning(job::Job)
isrunning(s::Server, jobdir::String)
```

Returns whether a job is running or not. If the job was submitted using `slurm`, a `QUEUED` status also counts as running.
