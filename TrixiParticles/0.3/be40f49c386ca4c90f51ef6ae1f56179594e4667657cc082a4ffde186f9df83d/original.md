```
interpolate_point(points_coords::Array{Array{Float64,1},1}, semi, ref_system, sol;
                  smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                  clip_negative_pressure=false)

interpolate_point(point_coords, semi, ref_system, sol;
                  smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                  clip_negative_pressure=false)
```

Performs interpolation of properties at specified points or an array of points in a TrixiParticles simulation.

When given an array of points (`points_coords`), it iterates over each point and applies interpolation individually. For a single point (`point_coords`), it performs the interpolation at that specific location. The interpolation utilizes the same kernel function of the SPH simulation to weigh contributions from nearby particles.

See also: [`interpolate_line`](@ref), [`interpolate_plane_2d`](@ref),           [`interpolate_plane_2d_vtk`](@ref), [`interpolate_plane_3d`](@ref), .

# Arguments

  * `points_coords`:  An array of point coordinates, for which to interpolate properties.
  * `point_coords`:   The coordinates of a single point for interpolation.
  * `semi`:           The semidiscretization used in the SPH simulation.
  * `ref_system`:     The reference system defining the properties of the SPH particles.
  * `sol`:            The current solution state from which properties are interpolated.

# Keywords

  * `smoothing_length=initial_smoothing_length(ref_system)`: The smoothing length used in the interpolation.
  * `cut_off_bnd=true`: Boolean to indicate if quantities should be set to `NaN` when the point                     is "closer" to the boundary than to the fluid in a kernel-weighted sense.                     Or, in more detail, when the boundary has more influence than the fluid                     on the density summation in this point, i.e., when the boundary particles                     add more kernel-weighted mass than the fluid particles.
  * `clip_negative_pressure=false`: One common approach in SPH models is to clip negative pressure                                 values, but this is unphysical. Instead we clip here during                                 interpolation thus only impacting the local interpolated value.

# Returns

  * For multiple points:  A `NamedTuple` of arrays containing interpolated properties at each point.
  * For a single point: A `NamedTuple` of interpolated properties at the point.

# Examples

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing); ref_system = fluid_system)
# For a single point
result = interpolate_point([1.0, 0.5], semi, ref_system, sol)

# For multiple points
points = [[1.0, 0.5], [1.0, 0.6], [1.0, 0.7]]
results = interpolate_point(points, semi, ref_system, sol)

# output
(density = ...)
```

!!! note
      * This function is particularly useful for analyzing gradients or creating visualizations along a specified line in the SPH simulation domain.
      * The interpolation accuracy is subject to the density of particles and the chosen smoothing length.
      * With `cut_off_bnd`, a density-based estimation of the surface is used which is not as

    accurate as a real surface reconstruction.

