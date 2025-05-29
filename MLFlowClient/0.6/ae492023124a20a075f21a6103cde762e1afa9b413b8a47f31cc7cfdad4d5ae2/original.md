```
searchexperiments(instance::MLFlow; max_results::Int64=20000, page_token::String="",
    filter::String="", order_by::Array{String}=String[],
    view_type::ViewType=ACTIVE_ONLY)
```

# Arguments

  * `instance`: [`MLFlow`](@ref) configuration.
  * `max_results`: Maximum number of experiments desired.
  * `page_token`: Token indicating the page of experiments to fetch.
  * `filter`: A filter expression over [`Experiment`](@ref) attributes and tags that allows returning a   subset of experiments. See [MLFlow documentation](https://mlflow.org/docs/latest/rest-api.html#search-experiments).
  * `order_by`: List of columns for ordering search results, which can include [`Experiment`](@ref)   name and id with an optional “DESC” or “ASC” annotation, where “ASC” is the default.
  * `view_type`: Qualifier for type of experiments to be returned. If unspecified, return   only active experiments. For more values, see [`ViewType`](@ref).

# Returns

  * Vector of [`Experiment`](@ref) that were found in the [`MLFlow`](@ref) instance.
  * The next page token if there are more results.
