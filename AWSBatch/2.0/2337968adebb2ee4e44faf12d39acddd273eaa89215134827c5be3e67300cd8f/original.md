```
wait(
    job::BatchJob,
    cond::Vector{JobState}=[RUNNING, SUCCEEDED],
    failure::Vector{JobState}=[FAILED];
    kwargs...,
)
```

Polls the batch job state until it hits one of the conditions in `cond`. The loop will exit if it hits a `failure` condition and will not catch any excpetions. The polling interval can be controlled with `delay` and `timeout` provides a maximum polling time.
