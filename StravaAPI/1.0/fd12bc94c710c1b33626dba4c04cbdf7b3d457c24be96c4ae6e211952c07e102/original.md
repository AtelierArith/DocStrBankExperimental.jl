Get Segment Effort Streams

Returns a set of streams for a segment effort completed by the authenticated athlete. Requires read_all scope.

Params:

  * id::Int64 (required)
  * keys::Vector{String} (required)
  * key*by*type::Bool (required)

Return: StreamSet, OpenAPI.Clients.ApiResponse
