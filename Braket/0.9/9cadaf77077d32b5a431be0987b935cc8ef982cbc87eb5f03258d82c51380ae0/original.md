```
log_metric(metric_name::String, value::Union{Float64, Int}; timestamp=time(), iteration_number=nothing)
```

Within a job script, log a metric with name `metric_name` and value `value` which can later be fetched *outside the job* with [`metrics`](@ref). A metric might be, for example, the loss of a training algorithm at each epoch, or similar.
