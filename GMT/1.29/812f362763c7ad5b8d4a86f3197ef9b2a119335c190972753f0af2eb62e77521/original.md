```
isclockwise(poly::Matrix{<:AbstractFloat}, view=(0.0,0.0,1.0)) -> Bool
```

Return true if the 2D/3D `poly` is clockwise when seen from the `view` direction.

### Example

```julia
poly = [0.0 0.0 0.0; 0.0 0.0 1.0; 0.0 1.0 1.0; 0.0 1.0 0.0; 0.0 0.0 0.0]
isclockwise(poly, (1.0,0.1,0.0))
```
