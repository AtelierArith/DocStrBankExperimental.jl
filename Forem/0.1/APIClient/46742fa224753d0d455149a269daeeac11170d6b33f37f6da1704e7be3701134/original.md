Suspend a User

This endpoint allows the client to suspend a user.  The user associated with the API key must have any 'admin' or 'moderator' role.  This specified user will be assigned the 'suspended' role. Suspending a user will stop the user from posting new posts and comments. It doesn't delete any of the user's content, just prevents them from creating new content while suspended. Users are not notified of their suspension in the UI, so if you want them to know about this, you must notify them.

Params:

  * id::Int64 (required)

Return: Nothing, OpenAPI.Clients.ApiResponse
