```
Point(x₁, x₂, ..., xₙ)
Point((x₁, x₂, ..., xₙ))
```

A point in `Dim`-dimensional space with coordinates in length units (default to meters).

The coordinates of the point are given with respect to the canonical Euclidean basis, and integer coordinates are converted to float.

## Examples

```julia
# 2D points
Point(1.0, 2.0) # add default units
Point(1.0m, 2.0m) # double precision as expected
Point(1f0km, 2f0km) # single precision as expected
Point(1m, 2m) # integer is converted to float by design

# 3D points
Point(1.0, 2.0, 3.0) # add default units
Point(1.0m, 2.0m, 3.0m) # double precision as expected
Point(1f0km, 2f0km, 3f0km) # single precision as expected
Point(1m, 2m, 3m) # integer is converted to float by design
```

### Notes

Integer coordinates are not supported because most geometric processing algorithms assume a continuous space. The conversion to float avoids `InexactError` and other unexpected results.
