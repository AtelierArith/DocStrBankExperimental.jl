```
MPS(::Type{T},
    sites::Vector{<:Index},
    states::Union{Vector{String},
                  Vector{Int},
                  String,
                  Int})
```

Construct a product state MPS of element type `T`, having site indices `sites`, and which corresponds to the initial state given by the array `states`. The input `states` may be an array of strings or an array of ints recognized by the `state` function defined for the relevant Index tag type. In addition, a single string or int can be input to create a uniform state.

# Examples

```julia
N = 10
sites = siteinds("S=1/2", N)
states = [isodd(n) ? "Up" : "Dn" for n in 1:N]
psi = MPS(ComplexF64, sites, states)
phi = MPS(sites, "Up")
```
