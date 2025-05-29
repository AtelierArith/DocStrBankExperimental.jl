Followers

This endpoint allows the client to retrieve a list of the followers they have.         "Followers" are users that are following other users on the website.         It supports pagination, each page will contain 80 followers by default.

Params:

  * page::Int64
  * per_page::Int64
  * sort::String

Return: Vector{GetFollowers200ResponseInner}, OpenAPI.Clients.ApiResponse
