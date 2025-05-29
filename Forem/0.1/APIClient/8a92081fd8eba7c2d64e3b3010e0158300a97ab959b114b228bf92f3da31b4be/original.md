Articles with a video

This endpoint allows the client to retrieve a list of articles that are uploaded with a video.  It will only return published video articles ordered by descending popularity.  It supports pagination, each page will contain 24 articles by default.

Params:

  * page::Int64
  * per_page::Int64

Return: Vector{VideoArticle}, OpenAPI.Clients.ApiResponse
