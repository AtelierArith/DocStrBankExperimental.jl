Published articles

This endpoint allows the client to retrieve a list of articles.  "Articles" are all the posts that users create on DEV that typically show up in the feed. They can be a blog post, a discussion question, a help thread etc. but is referred to as article within the code.  By default it will return featured, published articles ordered by descending popularity.  It supports pagination, each page will contain `30` articles by default.

Params:

  * page::Int64
  * per_page::Int64
  * tag::String
  * tags::String
  * tags_exclude::String
  * username::String
  * state::String
  * top::Int64
  * collection_id::Int64

Return: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
