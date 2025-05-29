```
save(job::Job)
```

Saves the job's calculations and `job.sh` submission script in `job.dir`. Some sanity checks will be performed on the validity of flags, execs, pseudopotentials, etc. The job will also be registered for easy retrieval at a later stage.

If a previous job is present in the job directory (indicated by a valid job script), it will be copied to the `.versions` sub directory as the previous version of `job`, and the version of `job` will be incremented. 
