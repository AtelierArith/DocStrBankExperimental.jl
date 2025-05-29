uvit_countrate2flux(channel, filter, cps)

Convert net source count rate to flux density or magnitude  for any of FUV/NUV broadband filters. This function is used by `uvit_aphot.jl`.

...

# Arguments

  * `channel::String`: UVIT channel FUV or NUV
  * `filter::String` : FUV or NUV filter e.g., "BaF2".
  * `cps::Float64` : Counts per second.

...
