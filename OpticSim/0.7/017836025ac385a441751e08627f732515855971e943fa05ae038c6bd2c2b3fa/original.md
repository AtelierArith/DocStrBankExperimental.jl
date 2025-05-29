```
MultiHologramInterface{T} <: OpticalInterface{T}
```

Interface to represent multiple overlapped [`HologramInterface`](@ref)s on a single surface. Each ray randomly selects an interface to use.

```julia
MultiHologramInterface(interfaces::Vararg{HologramInterface{T}})
MultiHologramInterface(interfaces::Vector{HologramInterface{T}})
```
