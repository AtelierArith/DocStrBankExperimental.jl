```
mutate([client::Client], mutation_name::Union{Alias, AbstractString}, args::AbstractDict, output_type::Type=Any; kwargs...)
```

Perform a mutation on the server, using the global client if `client` not supplied.

If no `output_fields` are supplied, none are returned.

By default `mutate` returns a `GQLReponse{Any}`, where the data for an individual mutation can be found by `gql_response.data[mutation_name]`.

The mutation uses the `endpoint` field of the `client`.

# Arguments

  * `client::Client`: GraphQL client (optional). If not supplied, [`global_graphql_client`](@ref) is used.
  * `mutation_name::Union{Alias, AbstractString}`: name of mutation_name.
  * `args`: dictionary of mutation argument key value pairs - can be nested with   dictionaries and vectors.
  * `output_type::Type=Any`: output data type for query response object. An object of type   `GQLResponse{output_type}` will be returned.For further information, see documentation   for `GQLResponse`.

# Keyword Arguments

  * `output_fields=String[]`: output fields to be returned. Can be a string, or   composed of dictionaries and vectors.
  * `direct_write=false`: if `true`, the query is formed by generating a string   from `args` directly, and the introspected schema is not used. Any ENUMs   must be wrapped in a `GQLEnum`. See [`directly_write_query_args`](@ref) for   more information.
  * `retries=1`: number of times the mutation will be attempted before erroring.
  * `readtimeout=0`: HTTP request timeout length. Set to 0 for no timeout.
  * `throw_on_execution_error=false`: set to `true` to throw an exception if the GraphQL server   response contains errors that occurred during execution.

See also: [`GQLResponse`](@ref)
