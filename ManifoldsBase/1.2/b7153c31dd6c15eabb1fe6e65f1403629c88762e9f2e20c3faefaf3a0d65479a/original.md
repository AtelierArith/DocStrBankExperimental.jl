```
SchildsLadderTransport <: AbstractVectorTransportMethod
```

Specify to use [`schilds_ladder`](@ref) as vector transport method within [`vector_transport_to`](@ref) or [`vector_transport_direction`](@ref), i.e.

Let $X∈ T_p\mathcal M$ be a tangent vector at $p∈\mathcal M$ and $q∈\mathcal M$ the point to transport to. Then

$$
P^{\mathrm{S}}_{q\gets p}(X) =
    \log_q\bigl( \operatorname{retr}_p ( 2\operatorname{retr}_p^{-1}c ) \bigr),
$$

where $c$ is the mid point between $q$ and $d=\exp_pX$.

This method employs the internal function [`schilds_ladder`](@ref)`(M, p, d, q)` that avoids leaving the manifold.

The name stems from the image of this paralleltogram in a repeated application yielding the image of a ladder. The approximation was proposed in [EhlersPiraniSchild:1972](@cite).

# Constructor

```julia
SchildsLadderTransport(
    retraction = ExponentialRetraction(),
    inverse_retraction = LogarithmicInverseRetraction(),
)
```

Construct the classical Schilds ladder that employs exp and log, i.e. as proposed in [EhlersPiraniSchild:1972](@cite). For an even cheaper transport these inner operations can be changed to an [`AbstractRetractionMethod`](@ref) `retraction` and an [`AbstractInverseRetractionMethod`](@ref) `inverse_retraction`, respectively.
