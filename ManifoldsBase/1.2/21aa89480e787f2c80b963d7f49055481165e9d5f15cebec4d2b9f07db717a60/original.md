```
QRRetraction <: AbstractRetractionMethod
```

Retractions that are based on a QR decomposition of the matrix / matrices for point and tangent vector on a [`AbstractManifold`](@ref)

!!! note "Technical Note"
    Though you would call e.g. [`retract`](@ref)`(M, p, X, QRRetraction())`, to implement a QR retraction, define [`retract_qr!`](@ref)`(M, q, p, X, t)` for your manifold `M`.

