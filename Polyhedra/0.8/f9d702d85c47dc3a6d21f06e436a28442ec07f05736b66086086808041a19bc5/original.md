```
vrep(rays::RayIt)
```

Creates a V-representation for the polyhedral cone of full dimension `d` equal to the conic hull of the rays `rays`.

### Examples

```julia
vrep([Ray([1, 0]), Ray([0, 1])])
```

creates a V-representation for positive orthant.
