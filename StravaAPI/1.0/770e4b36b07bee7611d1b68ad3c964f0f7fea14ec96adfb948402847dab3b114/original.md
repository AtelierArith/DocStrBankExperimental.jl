List Segment Efforts

Returns a set of the authenticated athlete's segment efforts for a given segment.  Requires subscription.

Params:

  * segment_id::Int64 (required)
  * start*date*local::ZonedDateTime
  * end*date*local::ZonedDateTime
  * per_page::Int64

Return: Vector{DetailedSegmentEffort}, OpenAPI.Clients.ApiResponse
