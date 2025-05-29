```
DifferentiatedRetractionVectorTransport{R<:AbstractRetractionMethod} <:
    AbstractVectorTransportMethod
```

A type to specify a vector transport that is given by differentiating a retraction. This can be introduced in two ways. Let $\mathcal M$ be a Riemannian manifold, $p∈\mathcal M$ a point, and $X,Y∈ T_p\mathcal M$ denote two tangent vectors at $p$.

Given a retraction (cf. [`AbstractRetractionMethod`](@ref)) $\operatorname{retr}$, the vector transport of `X` in direction `Y` (cf. [`vector_transport_direction`](@ref)) by differentiation this retraction, is given by

$$
\mathcal T^{\operatorname{retr}}_{p,Y}X
= D_Y\operatorname{retr}_p(Y)[X]
= \frac{\mathrm{d}}{\mathrm{d}t}\operatorname{retr}_p(Y+tX)\Bigr|_{t=0}.
$$

see [AbsilMahonySepulchre:2008](@cite), Section 8.1.2 for more details.

This can be phrased similarly as a [`vector_transport_to`](@ref) by introducing $q=\operatorname{retr}_pX$ and defining

$$
\mathcal T^{\operatorname{retr}}_{q \gets p}X = \mathcal T^{\operatorname{retr}}_{p,Y}X
$$

which in practice usually requires the [`inverse_retract`](@ref) to exists in order to compute $Y = \operatorname{retr}_p^{-1}q$.

# Constructor

```
DifferentiatedRetractionVectorTransport(m::AbstractRetractionMethod)
```
