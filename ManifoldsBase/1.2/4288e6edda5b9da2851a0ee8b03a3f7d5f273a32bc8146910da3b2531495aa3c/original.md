```
default_type(M::AbstractManifold, ft::FiberType)
```

Get the default type of points from the fiber `ft` of the fiber bundle based on manifold `M`. For example, call `default_type(MyManifold(), TangentSpaceType())` to get the default type of a tangent vector.
