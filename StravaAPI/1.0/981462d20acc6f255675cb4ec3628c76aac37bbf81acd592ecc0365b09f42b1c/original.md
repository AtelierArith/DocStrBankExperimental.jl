Get Activity

Returns the given activity that is owned by the authenticated athlete. Requires activity:read for Everyone and Followers activities. Requires activity:read_all for Only Me activities.

Params:

  * id::Int64 (required)
  * include*all*efforts::Bool

Return: DetailedActivity, OpenAPI.Clients.ApiResponse
