Tags

This endpoint allows the client to retrieve a list of tags that can be used to tag articles.  It will return tags ordered by popularity.  It supports pagination, each page will contain 10 tags by default.

Params:

  * page::Int64
  * per_page::Int64

Return: Vector{Tag}, OpenAPI.Clients.ApiResponse
