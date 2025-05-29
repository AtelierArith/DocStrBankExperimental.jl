Readinglist

This endpoint allows the client to retrieve a list of articles that were saved to a Users readinglist.         It supports pagination, each page will contain `30` articles by default

Params:

  * page::Int64
  * per_page::Int64

Return: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
