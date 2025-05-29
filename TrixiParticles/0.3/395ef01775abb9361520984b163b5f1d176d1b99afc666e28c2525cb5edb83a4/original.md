```
BoundaryZone(; plane, plane_normal, density, particle_spacing,
             initial_condition=nothing, extrude_geometry=nothing,
             open_boundary_layers::Integer, boundary_type=BidirectionalFlow())
```

Boundary zone for [`OpenBoundarySPHSystem`](@ref).

The specified plane (line in 2D or rectangle in 3D) will be extruded in the direction opposite to `plane_normal` to create a box for the boundary zone. There are three ways to specify the actual shape of the boundary zone:

1. Don't pass `initial_condition` or `extrude_geometry`. The boundary zone box will then be filled with boundary particles (default).
2. Specify `extrude_geometry` by passing a 1D shape in 2D or a 2D shape in 3D, which is then extruded in the direction opposite to `plane_normal` to create the boundary particles.

      * In 2D, the shape must be either an initial condition with 2D coordinates, which lies on the line specified by `plane`, or an initial condition with 1D coordinates, which lies on the line specified by `plane` when a y-coordinate of `0` is added.
      * In 3D, the shape must be either an initial condition with 3D coordinates, which lies in the rectangle specified by `plane`, or an initial condition with 2D coordinates, which lies in the rectangle specified by `plane` when a z-coordinate of `0` is added.
3. Specify `initial_condition` by passing a 2D initial condition in 2D or a 3D initial condition in 3D, which will be used for the boundary particles.

!!! note
    Particles outside the boundary zone box will be removed.


# Keywords

  * `plane`: Tuple of points defining a part of the surface of the domain.          The points must either span a line in 2D or a rectangle in 3D.          This line or rectangle is then extruded in upstream direction to obtain          the boundary zone.          In 2D, pass two points $(A, B)$, so that the interval $[A, B]$ is          the inflow surface.          In 3D, pass three points $(A, B, C)$, so that the rectangular inflow surface          is spanned by the vectors $\widehat{AB}$ and $\widehat{AC}$.          These two vectors must be orthogonal.
  * `plane_normal`: Vector defining the plane normal. It always points inside the fluid domain.
  * `boundary_type=BidirectionalFlow()`: Specify the type of the boundary. Available types are

      * `InFlow()` for an inflow boundary
      * `OutFlow()` for an outflow boundary
      * `BidirectionalFlow()` (default) for an bidirectional flow boundary
  * `open_boundary_layers`: Number of particle layers in the direction opposite to `plane_normal`.
  * `particle_spacing`: The spacing between the particles (see [`InitialCondition`](@ref)).
  * `density`: Particle density (see [`InitialCondition`](@ref)).
  * `initial_condition=nothing`: `InitialCondition` for the inflow particles.                              Particles outside the boundary zone will be removed.                              Do not use together with `extrude_geometry`.
  * `extrude_geometry=nothing`: 1D shape in 2D or 2D shape in 3D, which lies on the plane                             and is extruded upstream to obtain the inflow particles.                             See point 2 above for more details.

# Examples

```julia
# 2D
plane_points = ([0.0, 0.0], [0.0, 1.0])
plane_normal=[1.0, 0.0]

inflow = BoundaryZone(; plane=plane_points, plane_normal, particle_spacing=0.1, density=1.0,
                      open_boundary_layers=4, boundary_type=InFlow())

# 3D
plane_points = ([0.0, 0.0, 0.0], [1.0, 0.0, 0.0], [0.0, 1.0, 0.0])
plane_normal=[0.0, 0.0, 1.0]

outflow = BoundaryZone(; plane=plane_points, plane_normal, particle_spacing=0.1, density=1.0,
                       open_boundary_layers=4, boundary_type=OutFlow())

# 3D particles sampled as cylinder
circle = SphereShape(0.1, 0.5, (0.5, 0.5), 1.0, sphere_type=RoundSphere())

bidirectional_flow = BoundaryZone(; plane=plane_points, plane_normal, particle_spacing=0.1,
                                  density=1.0, extrude_geometry=circle, open_boundary_layers=4)
```

!!! warning "Experimental Implementation"
    This is an experimental feature and may change in any future releases.

