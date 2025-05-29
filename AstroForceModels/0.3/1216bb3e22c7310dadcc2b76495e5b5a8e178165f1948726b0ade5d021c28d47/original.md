Gravitational Harmonics Astro Model struct Contains information to compute the acceleration of a Gravitational Harmonics Model acting on a spacecraft.

# Fields

  * `gravity_model::AbstractGravityModel`: The gravitational potential model and coefficient data.
  * `eop_data::Union{EopIau1980,EopIau2000A}`: The data compute the Earth's orientation.
  * `order::Int`: The maximum order to compute the graviational potential to, a value of -1 compute the maximum order of the supplied model. (Default=-1)
  * `degree::Int`: The maximum degree to compute the graviational potential to, a value of -1 compute the maximum degree of the supplied model. (Default=-1)
