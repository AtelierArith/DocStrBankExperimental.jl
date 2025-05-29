```
searchmodelversions(instance::MLFlow, filter::String, max_results::Int64,
    order_by::String, page_token::String)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `filter`: String filter condition. See [MLFlow documentation](https://mlflow.org/docs/latest/rest-api.html#search-modelversions).
  * `max_results`: Maximum number of models desired.
  * `order_by`: List of columns to be ordered by including model name, version, stage with an   optional “DESC” or “ASC” annotation, where “ASC” is the default. Tiebreaks are done by   latest stage transition timestamp, followed by name ASC, followed by version DESC.
  * `page_token`: Pagination token to go to next page based on previous search query.

# Returns

  * Vector of [`ModelVersion`](@ref) that were found in the [`MLFlow`](@ref) instance.
  * The next page token if there are more results.
