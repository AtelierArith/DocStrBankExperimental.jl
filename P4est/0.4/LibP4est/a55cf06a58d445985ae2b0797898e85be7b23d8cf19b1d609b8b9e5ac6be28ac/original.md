The prototype for a function that [`p4est_iterate`](@ref) will execute wherever two quadrants share a face: the face can be a 2:1 hanging face, it does not have to be conformal.

!!! note
    the forest must be face balanced for [`p4est_iterate`](@ref)() to execute a callback function on faces (see [`p4est_balance`](@ref)()).


### Parameters

  * `info`:[in] information about a quadrant provided to the user
  * `user_data`:[in,out] the user context passed to [`p4est_iterate`](@ref)()
