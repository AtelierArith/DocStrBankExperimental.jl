Relativity Astro Model struct Contains information to compute the acceleration of relativity acting on a spacecraft.

# Fields

  * `central_body::ThirdBodyModel`: The data to compute the central body's graviational parameter.
  * `sun_body::ThirdBodyModel`: The data to compute the Sun's position, velocity, and graviational parameter.
  * `eop_data::Union{EopIau1980,EopIau2000A}`: Earth Orientation Parameter data.
  * `c::Number`: The speed of light [km/s].
  * `γ::Number`: Post-Newtonian Parameterization parameter. γ=1 in General Relativity.
  * `β::Number`: Post-Newtonian Parameterization parameter. β=1 in General Relativity.
  * `schwartzchild_effect::Bool`: Include the Schwartzchild relativity effect.
  * `lense_thirring_effect::Bool`: Include the Lense Thirring relativity effect.
  * `de_Sitter_effect::Bool`: Include the De Sitter relativity effect.
