Podcast Episodes

This endpoint allows the client to retrieve a list of podcast episodes.         "Podcast episodes" are episodes belonging to podcasts.         It will only return active (reachable) podcast episodes that belong to published podcasts available on the platform, ordered by descending publication date.         It supports pagination, each page will contain 30 articles by default.

Params:

  * page::Int64
  * per_page::Int64
  * username::String

Return: Vector{PodcastEpisodeIndex}, OpenAPI.Clients.ApiResponse
