Given a Cartesean position and velocity in the inertial frame, return the  state expressed in terms of  osculating orbital elements.

The osculating elements are assumed to be (in order):

1. *a*, Semi-major axis [m]
2. *e*, Eccentricity [dimensionless]
3. *i*, Inclination [rad]
4. *Ω*, Right Ascension of the Ascending Node (RAAN) [rad]
5. *ω*, Argument of Perigee [ramd]
6. *M*, Mean anomaly [rad]

Arguments:

  * x `x::AbstractArray{<:Real, 1}`: Cartesean inertial state. Returns position and velocity. [m; m/s]
  * `use_degrees:Bool`: If `true` interpret input will be interpreted as being in degrees, and output will be returned in degrees.
  * `GM::Real`: Gravitational constant of central body. Defaults to `SatelliteDynamics.GM_EARTH` if none is provided.

# Returns

  * x_oe `x::AbstractArray{<:Real, 1}`: Osculating orbital elements. See above for desription of the elements and their required order.
