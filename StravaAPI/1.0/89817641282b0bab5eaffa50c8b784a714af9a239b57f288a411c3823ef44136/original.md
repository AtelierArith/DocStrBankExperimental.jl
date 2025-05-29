Get Segment Streams

Returns the given segment's streams. Requires read_all scope for private segments.

Params:

  * id::Int64 (required)
  * keys::Vector{String} (required)
  * key*by*type::Bool (required)

Return: StreamSet, OpenAPI.Clients.ApiResponse
