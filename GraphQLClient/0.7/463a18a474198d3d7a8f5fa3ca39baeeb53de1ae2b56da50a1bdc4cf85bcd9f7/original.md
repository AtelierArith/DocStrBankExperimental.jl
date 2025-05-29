```
query([client::Client], query_name::Union{Alias, AbstractString}, output_type::Type=Any; kwargs...)
```

Perform a query on the server, using the global client if `client` not supplied.

If no `output_fields` are supplied, all possible fields (determined by introspection of `client`) are returned.

The query uses the `endpoint` field of the `client`.

By default `query` returns a `GQLReponse{Any}`, where the data for an individual query can be found by `gql_response.data[query_name]`.

# Arguments

  * `client::Client`: GraphQL client (optional). If not supplied, [`global_graphql_client`](@ref) is used.
  * `query_name::Union{Alias, AbstractString}`: name of query in server.
  * `output_type::Type=Any`: output data type for query response object. An object of type   `GQLResponse{output_type}` will be returned. For further information, see documentation   for `GQLResponse`.

# Keyword Arguments

  * `query_args=Dict()`: dictionary of query argument key value pairs - can be   nested with dictionaries and vectors.
  * `output_fields=String[]`: output fields to be returned. Can be a string, or   composed of dictionaries and vectors. If empty, `query` will attempt to return   all fields.
  * `direct_write=false`: if `true`, the query is formed by generating a string   from `query_args` directly, and the introspected schema is not used. Any ENUMs   must be wrapped in a `GQLEnum`. See [`directly_write_query_args`](@ref) for   more information.
  * `retries=1`: number of times the mutation will be attempted before erroring.
  * `readtimeout=0`: HTTP request timeout length. Set to 0 for no timeout.
  * `throw_on_execution_error=false`: set to `true` to throw an exception if the GraphQL server   response contains errors that occurred during execution.
  * `verbose=0`: set to 1, 2 for extra logging.

See also: [`GQLResponse`](@ref)
