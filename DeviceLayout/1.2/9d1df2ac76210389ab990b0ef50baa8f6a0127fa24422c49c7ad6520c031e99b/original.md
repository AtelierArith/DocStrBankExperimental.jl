```
transformation(c::GeometryStructure, d::GeometryReference, e::GeometryReference, f::GeometryReference...)
```

Given a geometry structure `c` containing [`GeometryReference`](@ref) `last(f)` in its tree of references, this function returns a `Transformations.ScaledIsometry` object that lets you translate from the coordinate system of `last(f)` to the coordinate system of `c`. This method is needed when you want to specify intermediate `GeometryReference`s explicitly.

For example, suppose for instance you have a hierarchy of coordinate systems, where coordinate system A references B1 and B2, which both reference C. Schematically, it might look like this:

```
a -- b1 -- c
  \      /
   \ b2 /
```

Coordinate system C appears in two places inside coordinate system A, owing to the fact that it is referenced by both B1 and B2. If you need to get the coordinate system of C via B2, then you need to do `transformation(coordinatesystemA, coordsysrefB2, coordsysrefC)`, rather than simply `transform(coordinatesystemA, coordsysrefC)`, because the latter will just take the first path to C available, via B1.
