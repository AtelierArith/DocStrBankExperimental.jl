List Club Activities

Retrieve recent activities from members of a specific club. The authenticated athlete must belong to the requested club in order to hit this endpoint. Pagination is supported. Athlete profile visibility is respected for all activities.

Params:

  * id::Int64 (required)
  * page::Int64
  * per_page::Int64

Return: Vector{ClubActivity}, OpenAPI.Clients.ApiResponse
