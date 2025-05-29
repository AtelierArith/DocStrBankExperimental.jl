Comments

This endpoint allows the client to retrieve all comments belonging to an article or podcast episode as threaded conversations.  It will return the all top level comments with their nested comments as threads. See the format specification for further details.

Params:

  * a_id::String
  * p_id::String

Return: Vector{Comment}, OpenAPI.Clients.ApiResponse
