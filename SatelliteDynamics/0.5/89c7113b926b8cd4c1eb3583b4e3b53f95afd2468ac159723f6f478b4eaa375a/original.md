Load Earth Orientation Data from a file. The caller must specify the product type to interpret the file as. If the product is not recognized, an error will be thrown.

Arguments:

  * `filepath::String` Path to the Earth Orientation Data file.
  * `product::Symbol` The IERS product type can be `:C04_20` or `:FINALS_2000`

Returns:

  * `EarthOrientationData` Earth Orientation Data object.
