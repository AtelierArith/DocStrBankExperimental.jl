The prototype for a function that [`p4est_iterate`](@ref) will execute wherever quadrants meet at a conformal corner

i.e. the callback will not execute on a hanging corner.

!!! note
    the forest does not need to be corner balanced for [`p4est_iterate`](@ref)() to correctly execute a callback function at corners, only face balanced (see [`p4est_balance`](@ref)()).


### Parameters

  * `info`:[in] information about a quadrant provided to the user
  * `user_data`:[in,out] the user context passed to [`p4est_iterate`](@ref)()
