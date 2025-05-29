`interp_chunk_to_grid_gp_temporal!( flux_out, var_out, chunk_of_spectrum, wavelengths )` Return spectra interpolated onto a grid of points using linear interpolation.

# Arguments:

  * flux_out: (results stored into this array)
  * var_out: (results stored into this array)
  * chunk*of*spectrum
  * wavelengths: AbstractRange or AbstractArray of locations where chunk is to be interpolated to
  * boost*factor: divide wavelengths by boost*factor

Optional Arguments:

  * Filter: Vector with pre-allocated workspace (if length>=1)

# Returns

  * flux_out
