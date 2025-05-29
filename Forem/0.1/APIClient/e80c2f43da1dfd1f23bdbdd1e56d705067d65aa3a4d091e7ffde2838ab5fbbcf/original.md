User's all articles

This endpoint allows the client to retrieve a list of all articles on behalf of an authenticated user.  "Articles" are all the posts that users create on DEV that typically show up in the feed. They can be a blog post, a discussion question, a help thread etc. but is referred to as article within the code.  It will return both published and unpublished articles with pagination.  Unpublished articles will be at the top of the list in reverse chronological creation order. Published articles will follow in reverse chronological publication order.  By default a page will contain 30 articles.

Params:

  * page::Int64
  * per_page::Int64

Return: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
