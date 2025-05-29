Callback function prototype to replace one set of quadrants with another.

This is used by extended routines when the quadrants of an existing, valid `p8est` are changed. The callback allows the user to make changes to newly initialized quadrants before the quadrants that they replace are destroyed.

If the mesh is being refined, num_outgoing will be 1 and num_incoming will be 8, and vice versa if the mesh is being coarsened.

### Parameters

  * `num_outgoing`:[in] The number of outgoing quadrants.
  * `outgoing`:[in] The outgoing quadrants: after the callback, the user_data, if `p8est`->data_size is nonzero, will be destroyed.
  * `num_incoming`:[in] The number of incoming quadrants.
  * `incoming`:[in,out] The incoming quadrants: prior to the callback, the user_data, if `p8est`->data*size is nonzero, is allocated, and the [`p8est*init_t`](@ref) callback, if it has been provided, will be called.
