Organization's users

This endpoint allows the client to retrieve a list of users belonging to the organization  It supports pagination, each page will contain `30` users by default.

Params:

  * username::String (required)
  * page::Int64
  * per_page::Int64

Return: Vector{User}, OpenAPI.Clients.ApiResponse
