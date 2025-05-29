List Athlete Activities

Returns the activities of an athlete for a specific identifier. Requires activity:read. Only Me activities will be filtered out unless requested by a token with activity:read_all.

Params:

  * before::Int64
  * after::Int64
  * page::Int64
  * per_page::Int64

Return: Vector{SummaryActivity}, OpenAPI.Clients.ApiResponse
