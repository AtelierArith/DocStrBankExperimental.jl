```
run!(job::Job; maxattempts=1, interval=1, delay=0, wait=false)
run!(job::Job, worker::Integer; maxattempts=1, interval=1, delay=0, wait=false)
```

Run a `Job` with a maximum number of attempts, with each attempt separated by `interval` seconds and an initial `delay` in seconds.
