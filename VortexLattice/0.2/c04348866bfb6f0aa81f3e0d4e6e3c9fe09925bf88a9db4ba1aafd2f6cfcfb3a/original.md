```
generate_rotor(rotor_file::String, data_path="."; optargs...)
```

Generate a grids, ratios, sections, invert_normals from a rotor file. Explained in the docs:

# Arguments

  * `rotor_file`: File with rotor parameters
  * `data_path`: Path to the rotor_file folder

# Keyword Arguments

  * `interpolate_airfoils_linear`: If true, the airfoil polars are interpolated linearly between the airfoils.  Defaults to false.
  * `interpolate_airfoils_akima`: If true, the airfoil polars are interpolated using Akima splines between the airfoils.
  * `zero_at_root`: If true, the airfoil positions are defined from the root,  otherwise from the center of the hub. Defaults to false.
  * `polar_in_radians`: If true, the airfoil polars are in radians, otherwise in degrees.  Defaults to false.
  * `turbine_flag`: If true, the rotor is a turbine, otherwise a propeller. Defaults to false.  If the true then the angle of attack is inverted in the nonlinear solver.
  * `clockwise`: If true, the rotor is intended to rotate clockwise, otherwise counter-clockwise. Defaults to false.
  * `ns`: Number of spanwise panels. Defaults to 10.
  * `nc`: Number of chordwise panels. Defaults to 1.
  * `spacing_s`: Spanwise spacing. Defaults to `VortexLattice.Sine()`.
  * `spacing_c`: Chordwise spacing. Defaults to `VortexLattice.Uniform()`.
  * `initial_azimuthal_angle`: Initial azimuthal angle of the rotor. Defaults to 0.0.
