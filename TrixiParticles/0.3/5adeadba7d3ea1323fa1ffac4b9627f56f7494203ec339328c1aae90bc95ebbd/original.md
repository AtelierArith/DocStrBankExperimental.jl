```
extrude_geometry(geometry; particle_spacing, direction, n_extrude::Integer,
                 velocity=zeros(length(direction)),
                 mass=nothing, density=nothing, pressure=0.0)
```

Extrude either a line, a plane or a shape along a specific direction. Returns an [`InitialCondition`](@ref).

# Arguments

  * `geometry`:           Either particle coordinates or an [`InitialCondition`](@ref)                       defining a 2D shape to extrude to a 3D volume, or two 2D points                       $(A, B)$ defining the interval $[A, B]$ to extrude to a plane                       in 2D, or three 3D points $(A, B, C)$ defining the parallelogram                       spanned by the vectors $\widehat{AB}$ and $\widehat {AC}$ to extrude                       to a parallelepiped.

# Keywords

  * `particle_spacing`:   Spacing between the particles. Can be omitted when `geometry` is an                       `InitialCondition` (unless `geometry.particle_spacing == -1`).
  * `direction`:          A vector that specifies the direction in which to extrude.
  * `n_extrude`:          Number of layers of particles created in the direction of extrusion.
  * `velocity`:           Either a function mapping each particle's coordinates to its velocity,                       or, for a constant fluid velocity, a vector holding this velocity.                       Velocity is constant zero by default.
  * `mass`:               Either `nothing` (default) to automatically compute particle mass from particle                       density and spacing, or a function mapping each particle's coordinates to its mass,                       or a scalar for a constant mass over all particles.
  * `density`:            Either a function mapping each particle's coordinates to its density,                       or a scalar for a constant density over all particles.
  * `pressure`:           Scalar to set the pressure of all particles to this value.                       This is only used by the [`EntropicallyDampedSPHSystem`](@ref) and                       will be overwritten when using an initial pressure function in the system.
  * `tlsph`:              With the [`TotalLagrangianSPHSystem`](@ref), particles need to be placed                       on the boundary of the shape and not one particle radius away, as for fluids.                       When `tlsph=true`, particles will be placed on the boundary of the shape.

# Examples

```jldoctest; output = false
# Extrude a line in 2D to a plane in 2D
p1 = [0.0, 0.0]
p2 = [1.0, 1.0]

direction = [-1.0, 1.0]

shape = extrude_geometry((p1, p2); direction, particle_spacing=0.1, n_extrude=4, density=1000.0)

# Extrude a parallelogram in 3D to a parallelepiped in 3D
p1 = [0.0, 0.0, 0.0]
p2 = [0.5, 1.0, 0.0]
p3 = [1.0, 0.2, 0.0]

direction = [0.0, 0.0, 1.0]

shape = extrude_geometry((p1, p2, p3); direction, particle_spacing=0.1, n_extrude=4, density=1000.0)

# Extrude a 2D shape (here: a disc) to a 3D shape (here: a cylinder)
shape = SphereShape(0.1, 0.5, (0.2, 0.4), 1000.0, n_layers=3,
                    sphere_type=RoundSphere(end_angle=pi))

direction = [0.0, 0.0, 1.0]

shape = extrude_geometry(shape; direction, particle_spacing=0.1, n_extrude=4, density=1000.0)

# output
┌ Info: The desired size is not a multiple of the particle spacing 0.1.
└ New particle spacing is set to 0.09387239731236392.
┌ Info: The desired size is not a multiple of the particle spacing 0.1.
└ New particle spacing is set to 0.09198039027185569.
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 3                                                                │
│ #particles: ………………………………………………… 144                                                              │
│ particle spacing: ………………………………… 0.1                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

!!! warning "Experimental Implementation"
    This is an experimental feature and may change in any future releases.

