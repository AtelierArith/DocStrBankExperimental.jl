Convert East-North-Zenith topocentric state to azimuth, elevation, and range.

Arguments:

  * `x::AbstractArray{<:Real, 1}`: East-North-Up state
  * `use_degrees:Bool`: If `true` returns result in units of degrees

Returns:

  * `azel::AbstractArray{<:Real, 1}`: Azimuth, elevation and range [rad; rad; m]
