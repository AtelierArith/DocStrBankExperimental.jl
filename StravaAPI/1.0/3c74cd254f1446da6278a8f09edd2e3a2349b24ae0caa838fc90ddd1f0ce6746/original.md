Update Activity

Updates the given activity that is owned by the authenticated athlete. Requires activity:write. Also requires activity:read_all in order to update Only Me activities

Params:

  * id::Int64 (required)
  * body::UpdatableActivity

Return: DetailedActivity, OpenAPI.Clients.ApiResponse
