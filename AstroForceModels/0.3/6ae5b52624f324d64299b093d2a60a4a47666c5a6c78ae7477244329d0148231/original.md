Drag Astro Model struct Contains information to compute the acceleration of a drag force on a spacecraft.

# Fields

  * `satellite_drag_model::AbstractSatelliteDragModel`: The satellite drag model for computing the ballistic coefficient.
  * `atmosphere_model::Symbol`: The atmospheric model for computing the density.
  * `eop_data::EopIau1980`: Earth orientation parameters to help compute the density with the atmospheric model.
