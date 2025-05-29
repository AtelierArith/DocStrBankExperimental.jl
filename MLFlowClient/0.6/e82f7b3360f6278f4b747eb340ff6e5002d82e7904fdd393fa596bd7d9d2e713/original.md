```
getmetrichistory(instance::MLFlow, run_id::String, metric_key::String;
    page_token::String="", max_results::Union{Int64, Missing}=missing)
```

Get a list of all values for the specified [`Metric`](@ref) for a given [`Run`](@ref).

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `run_id`: ID of the [`Run`](@ref) from which to fetch [`Metric`](@ref) values.
  * `metric_key`: Name of the [`Metric`](@ref) to fetch.
  * `page_token`: Token indicating the page of [`Metric`](@ref) history to fetch.
  * `max_results`: Maximum number of logged instances of a [`Metric`](@ref) for a   [`Run`](@ref) to return per call.

# Returns

  * A list of all historical values for the specified [`Metric`](@ref) in the specified   [`Run`](@ref).
  * The next page token if there are more results.
