```
struct MonoenergeticSource <: AbstractParticleSource
```

Particle source which emits monoenergetic particles, in either isotropic, directed ray or directed cone emission.

## Fields

  * `particle_type::String`: Particle type emitted by the source.
  * `energy::RealQuantity`: Energy of the particles emitted by the source.
  * `position::CartesianPoint`: Location of the source
  * `direction::CartesianVector`: Direction in which the source emits the particles.
  * `opening_angle::AngleQuantity`: Opening angle in case of directed cone emission.

## Examples

```julia
# Isotropic emission when no direction is passed
m1 = MonoenergeticSource("gamma", 2.615u"MeV", CartesianPoint(0.04, 0, 0.05))

# Directed ray emission when no opening_angle is passed
m2 = MonoenergeticSource("gamma", 2.615u"MeV", CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0))

# Directed cone emission when opening_angle is passed
m3 = MonoenergeticSource("gamma", 2.615u"MeV", CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0), 10u"°")
```

See also [`IsotopeSource`](@ref).
