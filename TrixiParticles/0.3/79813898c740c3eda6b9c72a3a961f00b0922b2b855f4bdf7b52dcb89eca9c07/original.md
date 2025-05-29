```
interpolate_plane_2d(min_corner, max_corner, resolution, semi, ref_system, sol;
                     smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                     clip_negative_pressure=false)
```

Interpolates properties along a plane in a TrixiParticles simulation. The region for interpolation is defined by its lower left and top right corners, with a specified resolution determining the density of the interpolation points.

The function generates a grid of points within the defined region, spaced uniformly according to the given resolution.

See also: [`interpolate_plane_2d_vtk`](@ref), [`interpolate_plane_3d`](@ref),           [`interpolate_line`](@ref), [`interpolate_point`](@ref).

# Arguments

  * `min_corner`: The lower left corner of the interpolation region.
  * `max_corner`: The top right corner of the interpolation region.
  * `resolution`: The distance between adjacent interpolation points in the grid.
  * `semi`:       The semidiscretization used for the simulation.
  * `ref_system`: The reference system for the interpolation.
  * `sol`:        The solution state from which the properties are interpolated.

# Keywords

  * `smoothing_length=initial_smoothing_length(ref_system)`: The smoothing length used in the interpolation.
  * `cut_off_bnd=true`: Boolean to indicate if quantities should be set to `NaN` when the point                     is "closer" to the boundary than to the fluid in a kernel-weighted sense.                     Or, in more detail, when the boundary has more influence than the fluid                     on the density summation in this point, i.e., when the boundary particles                     add more kernel-weighted mass than the fluid particles.
  * `clip_negative_pressure=false`: One common approach in SPH models is to clip negative pressure                                 values, but this is unphysical. Instead we clip here during                                 interpolation thus only impacting the local interpolated value.

# Returns

  * A `NamedTuple` of arrays containing interpolated properties at each point within the plane.

!!! note
      * The interpolation accuracy is subject to the density of particles and the chosen smoothing length.
      * With `cut_off_bnd`, a density-based estimation of the surface is used, which is not as accurate as a real surface reconstruction.


# Examples

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing); ref_system = fluid_system)
# Interpolating across a plane from [0.0, 0.0] to [1.0, 1.0] with a resolution of 0.2
results = interpolate_plane_2d([0.0, 0.0], [1.0, 1.0], 0.2, semi, ref_system, sol)

# output
(density = ...)
```
