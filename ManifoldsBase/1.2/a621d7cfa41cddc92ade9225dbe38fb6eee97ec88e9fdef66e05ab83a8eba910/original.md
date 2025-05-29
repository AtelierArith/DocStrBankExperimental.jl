```
ODEExponentialRetraction{T<:AbstractRetractionMethod, B<:AbstractBasis} <: AbstractRetractionMethod
```

Approximate the exponential map on the manifold by evaluating the ODE descripting the geodesic at 1, assuming the default connection of the given manifold by solving the ordinary differential equation

$$
\frac{d^2}{dt^2} p^k + Γ^k_{ij} \frac{d}{dt} p_i \frac{d}{dt} p_j = 0,
$$

where $Γ^k_{ij}$ are the Christoffel symbols of the second kind, and the Einstein summation convention is assumed.

# Constructor

```
ODEExponentialRetraction(
    r::AbstractRetractionMethod,
    b::AbstractBasis=DefaultOrthogonalBasis(),
)
```

Generate the retraction with a retraction to use internally (for some approaches) and a basis for the tangent space(s).
