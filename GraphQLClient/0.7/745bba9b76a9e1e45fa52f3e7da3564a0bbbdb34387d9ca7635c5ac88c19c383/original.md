```
Client(endpoint; headers=Dict(), introspect=true)
Client(endpoint, ws_endpoint; headers=Dict(), introspect=true)
```

GraphQL client. If just `endpoint` is provided, `ws_endpoint` is assumed to be the same as endpoint with "http" replaced by "ws".

By default, introspection will be performed on the client. This can be turned off by setting the `introspect` keyword argument to `false`.

# Fields - Public Interface

  * `endpoint::String`: endpoint for queries and mutations.
  * `ws_endpoint::String`: endpoint for subscriptions.
  * `headers::Dict`: contains client specific headers.
  * `introspection_complete::Bool`: set to `true` once introspection has been performed.
  * `queries::Vector{String}`: list of available queries.
  * `mutations::Vector{String}`: list of available mutations.
  * `subscriptions::Vector{String}`: list of available subscriptions.

# Fields - Internal Use

  * `type_to_fields_map::Dict{String, Dict{String, Dict{String, Any}}}`: maps GQL types   to their fields.
  * `query_to_type_map::Dict{String, String}`: maps GQL queries, mutations and   subscriptions to the type(s) of their outputs(s).
  * `query_to_args_map::Dict{String, Dict{String, String}}`: maps GQL queries, mutations   and subscriptions to their arguments and types.
  * `input_object_fields_to_type_map::Dict{String, Dict{String, String}}`: maps GQL input   objects to their fields/types.
  * `schema::Dict{String, Any}`: full schema of server.
  * `introspected_types::Dict{String, DataType}`: dictionary containing all introspected types.

# Examples

```julia
julia> client = Client("https://countries.trevorblades.com")
GraphQLClient Client
       endpoint: https://countries.trevorblades.com
    ws_endpoint: wss://countries.trevorblades.com

julia> client = Client("https://countries.trevorblades.com", "wss://countries.trevorblades.com")
GraphQLClient Client
       endpoint: https://countries.trevorblades.com
    ws_endpoint: wss://countries.trevorblades.com
```
