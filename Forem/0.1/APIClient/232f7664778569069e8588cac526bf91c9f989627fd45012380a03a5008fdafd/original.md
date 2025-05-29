create reaction

This endpoint allows the client to create a reaction to a specified reactable (eg, Article, Comment, or User). For examples:         * "Like"ing an Article will create a new "like" Reaction from the user for that Articles         * "Like"ing that Article a second time will return the previous "like"

Params:

  * category::String (required)
  * reactable_id::Int64 (required)
  * reactable_type::String (required)

Return: Nothing, OpenAPI.Clients.ApiResponse
