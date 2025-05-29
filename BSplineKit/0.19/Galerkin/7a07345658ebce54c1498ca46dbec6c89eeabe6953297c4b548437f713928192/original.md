```
galerkin_tensor(
    B::AbstractBSplineBasis,
    (D₁::Derivative, D₂::Derivative, D₃::Derivative),
    [T = Float64],
)
```

Compute 3D banded tensor appearing from quadratic terms in Galerkin method.

As with [`galerkin_matrix`](@ref), it is also possible to combine different functional bases by passing, instead of `B`, a tuple `(B₁, B₂, B₃)` of three `AbstractBSplineBasis`. For now, the first two bases, `B₁` and `B₂`, must have the same length.

The tensor is efficiently stored in a [`BandedTensor3D`](@ref) object.
