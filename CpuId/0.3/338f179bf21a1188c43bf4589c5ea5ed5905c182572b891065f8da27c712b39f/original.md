```
perf_gen_counters()
```

Determine the number of general purpose counters performance counters on the executing CPU.  Number of counters is given as per logical processor.

This information is only available if `cpufeature(PDCM) == true`.
