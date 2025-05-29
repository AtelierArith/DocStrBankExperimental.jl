`interp_chunk_to_grid_sinc!( flux_out, var_out, chunk_of_spectrum, wavelengths )` Return spectra interpolated onto a grid of points using sinc interpolation.

# Arguments:

  * flux_out: (results stored into this array)
  * var_out: (results stored into this array)
  * chunk*of*spectrum
  * wavelengths: AbstractRange or AbstractArray of locations where chunk is to be interpolated to

Optional Arguments:

  * Filter: Vector with pre-allocated workspace (if length>=1)

# Returns

  * flux_out
