Unpublish a User's Articles and Comments

This endpoint allows the client to unpublish all of the articles and comments created by a user.  The user associated with the API key must have any 'admin' or 'moderator' role.  This specified user's articles and comments will be unpublished and will no longer be visible to the public. They will remain in the database and will set back to draft status on the specified user's  dashboard. Any notifications associated with the specified user's articles and comments will be deleted.  Note this endpoint unpublishes articles and comments asychronously: it will return a 204 NO CONTENT status code immediately, but the articles and comments will not be unpublished until the request is completed on the server.

Params:

  * id::Int64 (required)

Return: Nothing, OpenAPI.Clients.ApiResponse
