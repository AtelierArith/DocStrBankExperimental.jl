```
searchruns(instance::MLFlow; experiment_ids::Array{String}=String[], filter::String="",
    run_view_type::ViewType=ACTIVE_ONLY, max_results::Int=1000,
    order_by::Array{String}=String[], page_token::String="")
```

Search for runs that satisfy expressions. Search expressions can use [`Metric`](@ref) and [`Param`](@ref) keys.

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `experiment_ids`: List of [`Experiment`](@ref) IDs to search over.
  * `filter`: A filter expression over params, metrics, and tags, that allows returning a   subset of runs. See [MLFlow documentation](https://mlflow.org/docs/latest/rest-api.html#search-runs).
  * `run_view_type`: Whether to display only active, only deleted, or all runs. Defaults to   only active runs.
  * `max_results`: Maximum number of runs desired.
  * `order_by`: List of columns to be ordered by, including attributes, params, metrics, and   tags with an optional “DESC” or “ASC” annotation, where “ASC” is the default.
  * `page_token`: Token indicating the page of runs to fetch.

# Returns

  * Vector of [`Run`](@ref) that were found in the specified experiments.
  * The next page token if there are more results.
