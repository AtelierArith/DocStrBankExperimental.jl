```
galerkin_tensor!(
    A::BandedTensor3D,
    B::AbstractBSplineBasis,
    (D₁::Derivative, D₂::Derivative, D₃::Derivative),
)
```

Compute 3D Galerkin tensor in-place.

See [`galerkin_tensor`](@ref) for details.
