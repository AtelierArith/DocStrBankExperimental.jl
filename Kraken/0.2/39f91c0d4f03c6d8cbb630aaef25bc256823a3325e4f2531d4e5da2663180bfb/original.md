````
PekerisUnderwaterEnv

A type representing the underwater environment in the Pekeris model.

# Fields
- `c1::T1`: The sound speed in the water column.
- `cb::T1`: The sound speed in the bottom half-space.
- `ρ1::T1`: The density of the water column.
- `ρb::T1`: The density of the bottom half-space.
- `depth::T1`: The depth of the water column.

# Constructor
```julia
PekerisUnderwaterEnv(c1::T1, cb, ρ1, ρb, depth) where {T1}
```

# Example
```julia
env = PekerisUnderwaterEnv(1500.0, 1600.0, 1000.0, 2000.0, 100.0)
```
````
