```
GRPFParams
```

Struct for holding values used by `RootsAndPoles` to stop iterating or split Delaunay triangles.

Default values are provided by `GRPFParams()`.

# Fields

  * `maxiterations::Int = 100`: the maximum number of refinement iterations before `grpf`   returns.
  * `maxnodes::Int = 500000`: the maximum number of Delaunay tessalation nodes before `grpf`   returns.
  * `skinnytriangle::Int = 3`: maximum ratio of the longest to shortest side length of   Delaunay triangles before they are split during `grpf` refinement iterations.
  * `tess_sizehint::Int = 5000`: provide a size hint to the total number of expected nodes in   the Delaunay tesselation. Setting this number approximately correct can improve   performance.
  * `tolerance::Float64 = 1e-9`: maximum allowed edge length of the tesselation defined in the   `origcoords` domain before returning.
  * `multithreading::Bool = false`: use `Threads.@threads` to run the user-provided function   `fcn` across the `DelaunayTriangulation`.
