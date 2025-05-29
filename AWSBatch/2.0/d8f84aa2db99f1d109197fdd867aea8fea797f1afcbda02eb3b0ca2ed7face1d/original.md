```
wait(
    cond::Function,
    job::BatchJob;
    timeout=600,
    delay=5
)
```

Polls the batch job state until it hits one of the conditions in `cond`. The loop will exit if it hits a `failure` condition and will not catch any excpetions. The polling interval can be controlled with `delay` and `timeout` provides a maximum polling time.

# Examples

```julia
julia> wait(state -> state < SUCCEEDED, job)
true
```
