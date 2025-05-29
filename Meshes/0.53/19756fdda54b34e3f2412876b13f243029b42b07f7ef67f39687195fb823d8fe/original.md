```
Vec(x₁, x₂, ..., xₙ)
Vec((x₁, x₂, ..., xₙ))
```

A geometric vector in `Dim`-dimensional space with coordinates in length units (default to meters) for linear algebra.

By default, integer coordinates are converted to float.

A vector can be obtained by subtracting two [`Point`](@ref) objects.

## Examples

```julia
A = Point(0.0, 0.0)
B = Point(1.0, 0.0)
v = B - A

# 2D vectors
Vec(1.0, 2.0) # add default units
Vec(1.0m, 2.0m) # double precision as expected
Vec(1f0km, 2f0km) # single precision as expected
Vec(1m, 2m) # integer is converted to float by design

# 3D vectors
Vec(1.0, 2.0, 3.0) # add default units
Vec(1.0m, 2.0m, 3.0m) # double precision as expected
Vec(1f0km, 2f0km, 3f0km) # single precision as expected
Vec(1m, 2m, 3m) # integer is converted to float by design
```

### Notes

A `Vec` is a subtype of `StaticVector` from StaticArrays.jl.
