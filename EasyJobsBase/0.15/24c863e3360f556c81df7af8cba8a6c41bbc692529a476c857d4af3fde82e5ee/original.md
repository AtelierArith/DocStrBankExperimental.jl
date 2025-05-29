```
timecostof(job::AbstractJob)
```

Return the time cost of the `job` since it started running.

If `nothing`, the `job` is still pending. If it is finished, return how long it took to complete.
