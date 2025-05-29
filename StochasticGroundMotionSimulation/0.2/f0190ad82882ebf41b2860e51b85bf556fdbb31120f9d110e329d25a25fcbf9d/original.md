```
create_spectral_moments(order::Vector{Int}, value::Vector{T}) where {T<:Real}
```

Create a `SpectralMoments` instance from vectors of order integers and moment values. Allows for encapsulation of named moments within the returned instance.
