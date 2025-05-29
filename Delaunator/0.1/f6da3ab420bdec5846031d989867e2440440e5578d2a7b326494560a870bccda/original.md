```
edgelines(t::Triangulation)
```

Return a generator that can be used with Makie's linesegments function to  display the edges of the triangulation. Each edge is only drawn once.

# Example

```
using GLMakie
t = triangulate(rand(StableRNG(1), Point2f, 10))
linesegments(collect(edgelines(rval)))
```
