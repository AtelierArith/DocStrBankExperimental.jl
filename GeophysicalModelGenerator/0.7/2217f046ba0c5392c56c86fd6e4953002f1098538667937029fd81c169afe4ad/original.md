```
CartData(xyz::Tuple{Array,Array,Array})
```

This creates a `CartData` struct if you have a Tuple with 3D coordinates as input.

# Example

```julia
julia> data = CartData(xyz_grid(-10:10,-5:5,0))
CartData
    size    : (21, 11, 1)
    x       ϵ [ -10.0 km : 10.0 km]
    y       ϵ [ -5.0 km : 5.0 km]
    z       ϵ [ 0.0 km : 0.0 km]
    fields  : (:Z,)
  attributes: ["note"]
```
