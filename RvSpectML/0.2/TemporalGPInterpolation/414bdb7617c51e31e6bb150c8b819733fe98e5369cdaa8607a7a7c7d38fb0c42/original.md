`interp*chunk*to*shifted*grid*gp*temporal( chunk*of*spectrum, wavelengths, boost_factor ) Return spectra interpolated onto a grid of points using linear interpolation.

# Arguments:

  * chunk*of*spectrum
  * wavelengths: AbstractRange or AbstractArray of locations where chunk is to be interpolated to
  * boost*factor: divide wavelengths by boost*factor

Optional Arguments:

  * Filter: Vector with pre-allocated workspace (if length>=1)

# Returns

  * flux_out
