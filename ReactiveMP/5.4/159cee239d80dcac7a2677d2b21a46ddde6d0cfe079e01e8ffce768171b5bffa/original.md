Creates a flow model with uninitialized parameters.

Input arguments:

  * `dim::Int` - input dimensionality.
  * `layers<:NTuple{N,AbstractLayer}` - arbitrarily sized tuple containing abstractlayers.

Return arguments:

  * `::Flowmodel` - model containing layers of which are appropriately sized according to the input dimensionality.
