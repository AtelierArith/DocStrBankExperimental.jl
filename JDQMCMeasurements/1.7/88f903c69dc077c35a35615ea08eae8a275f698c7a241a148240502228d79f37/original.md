```
susceptibility(S::AbstractVector{T}, Δτ::E) where {T<:Number, E<:AbstractFloat}
```

Calculate the suceptibility

$$
\chi = \int_0^\beta S(\tau) d\tau,
$$

where the correlation data is stored in `S`. The integration is performed using Simpson's method using a step size of `Δτ`.
