```
struct IsotopeSource <: AbstractParticleSource
```

Particle source which emits particles based on a defined decay chain, in either isotropic, directed ray or directed cone emission.

## Fields

  * `Z::Int32`: Atomic number of the mother nucleus.
  * `A::Int32`: Mass number of the mother nucleus.
  * `ionCharge::Float64`: Charge of the mother nucleus.
  * `excitEnergy::Float64`: Excitation energy of the mother nucleus.
  * `position::CartesianPoint`: Location of the source
  * `direction::CartesianVector`: Direction in which the source emits the particles.
  * `opening_angle::AngleQuantity`: Opening angle in case of directed cone emission.

## Examples

```julia
# Isotropic emission when no direction is passed
i1 = IsotopeSource(82, 212, 0, 0, CartesianPoint(0.04, 0, 0.05))
   
# Directed ray emission when no opening_angle is passed
i2 = IsotopeSource(82, 212, 0, 0, CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0))

# Directed cone emission when opening_angle is passed
i3 = IsotopeSource(82, 212, 0, 0, CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0), 10u"°")
```

See also [`MonoenergeticSource`](@ref).
