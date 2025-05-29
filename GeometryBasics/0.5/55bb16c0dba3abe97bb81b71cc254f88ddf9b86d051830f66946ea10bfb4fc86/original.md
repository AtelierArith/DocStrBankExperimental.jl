```
Tessellation(primitive, nvertices)
```

When generating a mesh from an abstract geometry, we can typically generate it at different levels of detail, i.e. with different amounts of vertices. The `Tessellation` wrapper allows you to specify this level of detail. When generating a mesh from a tessellated geometry, the added information will be passed to `coordinates`, `faces`, etc.

```julia
sphere = Sphere(Point3f(0), 1)
m1 = mesh(sphere) # uses a default value for tessellation
m2 = mesh(Tessellation(sphere, 64)) # uses 64 for tessellation
length(coordinates(m1)) != length(coordinates(m2))
```

For grid based tessellation, you can also use a tuple:

```julia
rect = Rect2(0, 0, 1, 1)
Tessellation(rect, (5, 5))
```
