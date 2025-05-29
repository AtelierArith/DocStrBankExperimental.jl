```
bt, cdata = basictriangulation(IntType=Int32,] [FloatType=Float64,] [points];[sizehint=length(points),] [tol])
```

Allocate a basic triangulation structure and associated compute data in order to implement the Deluantor method. 

**This method does not actaully compute a triangulation, but only allocates the data. See `triangulate` or `update!` for the computational methods.**

## The triangulation data structure

These data structures are explained at https://mapbox.github.io/delaunator/  (but here, all the indices have been modified a little).

  * `triangles`: a length T array of 3 tuples, where each tuple is a triangle
  * `halfedges`: The halfedge index for the edge in the triangle array. The halfedges for    triangle t are 3(t-1)+1, 3(t-1)+2, 3(t-2)+3. Each halfedge index gives the entry   of the other halfedge.
  * `points` a copy of the input set of points
