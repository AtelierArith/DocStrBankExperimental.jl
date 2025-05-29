```
searchregisteredmodels(instance::MLFlow, filter::String, max_results::Int64,
    order_by::String, page_token::String)
```

# Arguments

  * `instance:` [`MLFlow`](@ref) configuration.
  * `filter`: String filter condition. See [MLFlow documentation](https://mlflow.org/docs/latest/rest-api.html#search-registeredmodels).
  * `max_results`: Maximum number of models desired.
  * `order_by`: List of columns for ordering search results, which can include model name   and last updated timestamp with an optional “DESC” or “ASC” annotation, where “ASC” is   the default. Tiebreaks are done by model name ASC.
  * `page_token`: Pagination token to go to the next page based on a previous search query.

# Returns

  * Vector of [`RegisteredModel`](@ref) that were found in the [`MLFlow`](@ref) instance.
  * The next page token if there are more results.
