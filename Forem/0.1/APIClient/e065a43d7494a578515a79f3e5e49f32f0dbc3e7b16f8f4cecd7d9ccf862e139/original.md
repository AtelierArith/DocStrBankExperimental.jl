Unpublish an article

This endpoint allows the client to unpublish an article.  The user associated with the API key must have any 'admin' or 'moderator' role.  The article will be unpublished and will no longer be visible to the public. It will remain in the database and will set back to draft status on the author's posts dashboard. Any notifications associated with the article will be deleted. Any comments on the article will remain.

Params:

  * id::Int64 (required)
  * note::String

Return: Nothing, OpenAPI.Clients.ApiResponse
