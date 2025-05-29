List Activity Kudoers

Returns the athletes who kudoed an activity identified by an identifier. Requires activity:read for Everyone and Followers activities. Requires activity:read_all for Only Me activities.

Params:

  * id::Int64 (required)
  * page::Int64
  * per_page::Int64

Return: Vector{SummaryAthlete}, OpenAPI.Clients.ApiResponse
