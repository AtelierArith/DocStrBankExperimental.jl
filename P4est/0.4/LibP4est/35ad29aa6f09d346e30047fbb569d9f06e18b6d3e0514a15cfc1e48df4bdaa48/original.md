The prototype for a function that [`p8est_iterate`](@ref) will execute wherever the corner is a corner for all quadrants that touch it

i.e. the callback will not execute on a corner that sits on a hanging face or edge.

!!! note
    the forest does not need to be corner balanced for [`p8est_iterate`](@ref)() to execute a callback function at corners, only face and edge balanced.


### Parameters

  * `info`:[in] information about a quadrant provided to the user
  * `user_data`:[in,out] the user context passed to [`p8est_iterate`](@ref)()
