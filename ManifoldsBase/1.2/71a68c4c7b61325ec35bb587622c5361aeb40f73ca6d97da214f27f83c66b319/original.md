```
QRInverseRetraction <: AbstractInverseRetractionMethod
```

Inverse retractions that are based on a QR decomposition of the matrix / matrices for point and tangent vector on a [`AbstractManifold`](@ref)

!!! note "Technical Note"
    Though you would call e.g. [`inverse_retract`](@ref)`(M, p, q, QRInverseRetraction())`, to implement an inverse QR retraction, define [`inverse_retract_qr!`](@ref)`(M, X, p, q)` for your manifold `M`.

