```julia
struct RigidTransform{T<:Real}
```

Rigid transformation represented by a single rotation (around a specific center of rotation) and translation.

# Constructors

```julia
RigidTransform(r::RotMatrix3{T}, t::Vector3{T}, center::Vector3{T} = zeros(Vector3{T}))
RigidTransform(r::Matrix3{T}, t::Vector3{T}, center::Vector3{T} = zeros(Vector3{T}))
```

Creates a new `RigidTransform{T}` from the given rotation `r`, `center` of rotation, and translation `t`.

!!! note
    From the documentation of Rotations.jl:

    > The given `Matrix3{T}` should have the property `I =RR^T`, but this isn't enforced by the constructor.

