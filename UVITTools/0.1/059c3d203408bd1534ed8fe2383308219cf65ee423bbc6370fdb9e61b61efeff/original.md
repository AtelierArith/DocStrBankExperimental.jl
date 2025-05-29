`write_uvit_grating_phafile(uvit_detector, uvit_grating, channels, counts, exptime_sec[, phafile="phafile.pha"])`

Write OGIP compatible PHA spectral file from grating count spectra - channel vs counts.

This function is used by grating spectroscopy tools. ...

# Arguments

  * `uvit_detector::String`: FUV or NUV.
  * `uvit_grating::String`: One of the UVIT gratings - FUV-Grating1, FUV-Grating2, NUV-Grating.
  * `channels::Array{Int64}`: An array of spectral channels.
  * `counts::Array{Float64}`: An array of counts corresponding to the spectral channel array.
  * `exposure_time_sec::Float64`: Exposure time (s).

# Optional

  * `phafile::String`: Name of the PHA spectral file to be generated.

...
