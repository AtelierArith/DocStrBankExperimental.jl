```
interpolate_line(start, end_, n_points, semi, ref_system, sol; endpoint=true,
                 smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                 clip_negative_pressure=false)
```

Interpolates properties along a line in a TrixiParticles simulation. The line interpolation is accomplished by generating a series of evenly spaced points between `start` and `end_`. If `endpoint` is `false`, the line is interpolated between the start and end points, but does not include these points.

See also: [`interpolate_point`](@ref), [`interpolate_plane_2d`](@ref),           [`interpolate_plane_2d_vtk`](@ref), [`interpolate_plane_3d`](@ref).

# Arguments

  * `start`:      The starting point of the line.
  * `end_`:       The ending point of the line.
  * `n_points`:   The number of points to interpolate along the line.
  * `semi`:       The semidiscretization used for the simulation.
  * `ref_system`: The reference system for the interpolation.
  * `sol`:        The solution state from which the properties are interpolated.

# Keywords

  * `endpoint=true`: A boolean to include (`true`) or exclude (`false`) the end point in the interpolation.
  * `smoothing_length=initial_smoothing_length(ref_system)`: The smoothing length used in the interpolation.
  * `cut_off_bnd=true`: Boolean to indicate if quantities should be set to `NaN` when the point                     is "closer" to the boundary than to the fluid in a kernel-weighted sense.                     Or, in more detail, when the boundary has more influence than the fluid                     on the density summation in this point, i.e., when the boundary particles                     add more kernel-weighted mass than the fluid particles.
  * `clip_negative_pressure=false`: One common approach in SPH models is to clip negative pressure                                 values, but this is unphysical. Instead we clip here during                                 interpolation thus only impacting the local interpolated value.

# Returns

  * A `NamedTuple` of arrays containing interpolated properties at each point along the line.

!!! note
      * This function is particularly useful for analyzing gradients or creating visualizations along a specified line in the SPH simulation domain.
      * The interpolation accuracy is subject to the density of particles and the chosen smoothing length.
      * With `cut_off_bnd`, a density-based estimation of the surface is used which is not as accurate as a real surface reconstruction.


# Examples

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing); ref_system = fluid_system)
# Interpolating along a line from [1.0, 0.0] to [1.0, 1.0] with 5 points
results = interpolate_line([1.0, 0.0], [1.0, 1.0], 5, semi, ref_system, sol)

# output
(density = ...)
```
