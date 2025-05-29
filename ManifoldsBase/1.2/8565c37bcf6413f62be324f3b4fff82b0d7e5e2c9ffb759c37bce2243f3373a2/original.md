```
ScaledVectorTransport{T} <: AbstractVectorTransportMethod
```

Introduce a scaled variant of any [`AbstractVectorTransportMethod`](@ref) `T`, as introduced in [SatoIwai:2013](@cite) for some $X∈ T_p\mathcal M$ as

$$
    \mathcal T^{\mathrm{S}}(X) = \frac{\lVert X\rVert_p}{\lVert \mathcal T(X)\rVert_q}\mathcal T(X).
$$

Note that the resulting point `q` has to be known, i.e. for [`vector_transport_direction`](@ref) the curve or more precisely its end point has to be known (via an exponential map or a retraction). Therefore a default implementation is only provided for the [`vector_transport_to`](@ref)

# Constructor

```
ScaledVectorTransport(m::AbstractVectorTransportMethod)
```
