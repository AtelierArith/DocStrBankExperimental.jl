```
polytriangulate(plist::Vector{Point}; epsilon = -0.01)
```

Triangulate the polygon in `plist`.

This uses the Bowyer–Watson/Delaunay algorithm to make triangles. It returns an array of triangular polygons.

!!! note
    This experimental polygon function is not very efficient, because it first copies the list of points (to avoid modifying the original), and sorts it, before making triangles.

