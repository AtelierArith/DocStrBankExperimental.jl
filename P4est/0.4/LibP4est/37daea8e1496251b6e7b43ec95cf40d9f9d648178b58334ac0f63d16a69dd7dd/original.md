The prototype for a function that [`p8est_iterate`](@ref) will execute wherever the edge is an edge of all quadrants that touch it i.e. the callback will not execute on an edge the sits on a hanging face.

!!! note
    the forest must be edge balanced for [`p8est_iterate`](@ref)() to execute a callback function on edges.


### Parameters

  * `info`:[in] information about a quadrant provided to the user
  * `user_data`:[in,out] the user context passed to [`p8est_iterate`](@ref)()
