```julia
struct Thruster
```

Defines a Hall thruster from a name, geometry, magnetic field. The thruster may also be shielded, in which case the wall electron temperature is assumed to be equal to the anode electron temperature inside the discharge channel.

# Fields

  * `name::String`: Name of the thruster. Not used during the simulation, but useful for certain cases.

  * `geometry::HallThruster.Geometry1D`: The thruster geometry

  * `magnetic_field::HallThruster.MagneticField`: Contains a magnetic field at discrete axial locations

  * `shielded::Bool`: Whether the thruster is magnetically-shielded
