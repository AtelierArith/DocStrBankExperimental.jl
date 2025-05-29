```
global_position(sys::System, site::Site)
```

Position of a [`Site`](@ref) in global coordinates.

To precompute a full list of positions, one can use [`eachsite`](@ref) as below:

```julia
pos = [global_position(sys, site) for site in eachsite(sys)]
```
