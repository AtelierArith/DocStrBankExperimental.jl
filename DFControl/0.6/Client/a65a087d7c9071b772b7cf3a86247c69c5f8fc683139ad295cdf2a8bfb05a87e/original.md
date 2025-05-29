```
abort(job::Job)
```

Will try to remove the job from the scheduler's queue. If the last running calculation happened to be a `Calculation{QE}`, the correct abort file will be written. For other codes the process is not smooth, and restarting is not guaranteed.
