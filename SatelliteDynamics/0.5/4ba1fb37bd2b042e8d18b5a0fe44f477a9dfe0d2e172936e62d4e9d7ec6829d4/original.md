Earth Orientation Data object. This object stores Earth Orientation Parameters (EOP) and Celestial Intermediate Pole (CIP) offsets.  The object is used to compute the Earth Orientation Parameters for a given Modified Julian Date (MJD).

Attributes:

  * `data::Dict{Int, Tuple{Float64, Float64, Float64}}` EOP data stored as a dictionary with MJD as the key and a tuple of (UT1-UTC [s], xp [rad], yp [rad]) as the value.
  * `last_eop_data::Int` Last MJD value in the EOP data.
  * `dXdYData::Dict{Int, Tuple{Float64, Float64}}` CIP offsets stored as a dictionary with MJD as the key and a tuple of (dX [rad], dY [rad]) as the value.
  * `last_dxdy_mjd::Int` Last MJD value in the dX/dY data.
