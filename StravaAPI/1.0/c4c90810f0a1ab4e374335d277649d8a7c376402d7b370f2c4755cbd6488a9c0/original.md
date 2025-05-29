Create an Activity

Creates a manual activity for an athlete, requires activity:write scope.

Params:

  * name::String (required)
  * sport_type::String (required)
  * start*date*local::ZonedDateTime (required)
  * elapsed_time::Int64 (required)
  * type::String
  * description::String
  * distance::Float32
  * trainer::Int64
  * commute::Int64

Return: DetailedActivity, OpenAPI.Clients.ApiResponse
