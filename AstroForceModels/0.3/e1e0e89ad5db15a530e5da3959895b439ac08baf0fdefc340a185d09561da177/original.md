Third Body Model Astro Model struct Contains information to compute the acceleration of a third body force acting on a spacecraft.

# Fields

  * `body::CelestialBody`: Celestial body acting on the craft.
  * `ephem_type::AbstractEphemerisType`: Ephemeris type used to compute body's position. Options are currently Vallado().
