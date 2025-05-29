```
start(job::JobInfo, ARGS)
```

Call this from your job script to start the Carlo command line interface.

If for any reason you do not want to use job scripts, you can directly schedule a job using

```
start(Carlo.MPIScheduler, job)
```
