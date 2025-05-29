Compute the Moon's position in the EME2000 inertial frame through the use of low-precision analytical functions.

Argument:

  * `epc::Epoch`: Epoch

Returns:

  * `r_moon::AbstractArray{<:Real, 1}`: Position vector of the Moon in the Earth-centered inertial fame.

Notes:

1. The EME2000 inertial frame is for most purposes equivalent to the GCRF frame.

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.70-73.
