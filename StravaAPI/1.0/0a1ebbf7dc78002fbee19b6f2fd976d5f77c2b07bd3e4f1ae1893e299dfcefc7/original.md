List Athlete Routes

Returns a list of the routes created by the authenticated athlete. Private routes are filtered out unless requested by a token with read_all scope.

Params:

  * page::Int64
  * per_page::Int64

Return: Vector{Route}, OpenAPI.Clients.ApiResponse
