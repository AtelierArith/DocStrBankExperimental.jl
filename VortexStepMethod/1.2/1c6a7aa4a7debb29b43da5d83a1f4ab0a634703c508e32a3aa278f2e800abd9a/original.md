```
RamAirWing(obj_path, dat_path; kwargs...)
```

Create a ram-air wing model from 3D geometry and airfoil data files.

This constructor builds a complete aerodynamic model by:

1. Loading or generating wing geometry from the .obj file
2. Creating aerodynamic polars from the airfoil .dat file
3. Computing inertial properties and coordinate transformations
4. Setting up control surfaces and panel distribution

# Arguments

  * `obj_path`: Path to .obj file containing 3D wing geometry
  * `dat_path`: Path to .dat file containing 2D airfoil profile

# Keyword Arguments

  * `crease_frac=0.9`: Normalized trailing edge hinge location (0-1)
  * `wind_vel=10.0`: Reference wind velocity for XFoil analysis (m/s)
  * `mass=1.0`: Wing mass (kg)
  * `n_panels=56`: Number of aerodynamic panels across wingspan
  * `n_groups=4`: Number of control groups for deformation
  * `n_sections=n_panels+1`: Number of spanwise cross-sections
  * `align_to_principal=false`: Align body frame to principal axes of inertia
  * `spanwise_distribution=UNCHANGED`: Panel distribution type
  * `remove_nan=true`: Interpolate NaN values in aerodynamic data
  * `alpha_range=deg2rad.(-5:1:20)`: Angle of attack range for polars (rad)
  * `delta_range=deg2rad.(-5:1:20)`: Trailing edge deflection range for polars (rad)
  * prn=true: if info messages shall be printed

# Returns

A fully initialized `RamAirWing` instance ready for aerodynamic simulation.

# Example

```julia
# Create a ram-air wing from geometry files
wing = RamAirWing(
    "path/to/wing.obj",
    "path/to/airfoil.dat";
    mass=1.5,
    n_panels=40,
    n_groups=4
)
```
