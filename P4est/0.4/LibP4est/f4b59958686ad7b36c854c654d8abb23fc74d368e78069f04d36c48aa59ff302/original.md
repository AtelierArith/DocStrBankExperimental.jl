Callback function prototype to transfer information from outgoing layers to incoming layers.

This is used by extended routines when the layers of an existing, valid `p6est` are changed. The callback allows the user to make changes to newly initialized layers before the layers that they replace are destroyed.

### Parameters

  * `num_outcolumns`:[in] The number of columns that contain the outgoing layers: will be either 1 or 4.
  * `num_outlayers`:[in] The number of outgoing layers: will be either 1 (a single layer is being refined), 2 (two layers are being vertically coarsened), or 4 (four layers are being horizontally coarsened).
  * `outcolumns`:[in] The columns of the outgoing layers
  * `outlayers`:[in] The outgoing layers: after the callback, the user_data, if `p6est`->data_size is nonzero, will be destroyed.
  * `num_incolumns`:[in] The number of columns that contain the outgoing layers: will be either 1 or 4.
  * `num_inlayers`:[in] The number of incoming layers: will be either 1 (coarsening), 2 (vertical refinement), or 4 (horizontal refinement)
  * `incolumns`:[in] The columns of the incoming layers
  * `inlayers`:[in,out] The incoming layers: prior to the callback, the user_data, if `p6est`->data*size is nonzero, is allocated, and the [`p6est*init_t`](@ref) callback, if it has been provided, will be called.
