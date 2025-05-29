Get Activity Streams

Returns the given activity's streams. Requires activity:read scope. Requires activity:read_all scope for Only Me activities.

Params:

  * id::Int64 (required)
  * keys::Vector{String} (required)
  * key*by*type::Bool (required)

Return: StreamSet, OpenAPI.Clients.ApiResponse
