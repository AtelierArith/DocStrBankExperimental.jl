Determines the Earth's albedo at a satellite for a given set of reflectivity data.  First divides the Earth's surface into a set of cells (determined by the size of the refl data),  and then determines which cells are visible by both the satellite and the Sun. This is  then used to determine how much sunlight is reflected by the Earth towards the satellite.

Arguments:

  * sat: Vector from center of Earth to satellite                                     |  SVector{3, Float64}
  * sun: Vector from center of Earth to Sun                                           |  SVector{3, Flaot64}
  * refl_data:  Matrix containing the averaged reflectivity data for each cell        |  Array{Float64, 2}
  * Rₑ:   (Optional) Average radius of the Earth (default is 6371010 m)               |  Scalar
  * AM₀:  (Optional) Solar irradiance  (default is 1366.9)                            |  Scalar

Returns:

  * cell*albedos: Matrix with each element corresponding to the albedo coming from                    the corresponding cell on the surface of the earth            | [num*lat x num_lon]
