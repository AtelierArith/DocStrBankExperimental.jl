```
CSGGenerator{T<:Real}
```

This is the type you should use when making CSG objects. This type allows for the construction of [`CSGTree`](@ref) objects with different transforms. When the generator is evaluated, all transforms are propagated down to the [`LeafNode`](@ref)s and stored there.

# Example

```julia
a = Cylinder(1.0,1.0)
b = Plane([0.0,0.0,1.0], [0.0,0.0,0.0])
generator = a ∩ b
# now make a csg object that can be ray traced
csgobj = generator(Transform(1.0,1.0,2.0))
```
