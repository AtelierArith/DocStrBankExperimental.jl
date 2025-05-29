```
logbatch(instance::MLFlow, run_id::String; metrics::MLFlowUpsertData{Metric},
    params::MLFlowUpsertData{Param}, tags::MLFlowUpsertData{Tag})
logbatch(instance::MLFlow, run::Run; metrics::Array{Metric},
    params::MLFlowUpsertData{Param}, tags::MLFlowUpsertData{Tag})
```

Log a batch of metrics, params, and tags for a [`Run`](@ref). In case of error, partial data may be written.

For more information about this function, check [MLFlow official documentation](https://mlflow.org/docs/latest/rest-api.html#log-batch).

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) to log under.
  * `metrics`: A collection of [`Metric`](@ref) to log.
  * `params`: A collection of [`Param`](@ref) to log.
  * `tags`: A collection of [`Tag`](@ref) to log.

**Note**: A single request can contain up to 1000 metrics, and up to 1000 metrics, params, and tags in total.

# Returns

`true` if successful. Otherwise, raises exception.
