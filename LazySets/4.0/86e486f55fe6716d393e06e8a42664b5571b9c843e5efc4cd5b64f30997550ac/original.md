```
triangulate(X::LazySet; [algorithm]::String="delaunay", [kwargs]...)
```

Compute a triangulation of the given polytopic set.

### Input

  * `X`         – polytopic set
  * `algorithm` – (optional; default: `delaunay`) string to choose the                type of triangulation
  * `kwargs`    – further keyword arguments passed to the algorithm

### Output

A union of polytopes in vertex representation.

### Algorithm

The algorithm is selected with the argument `algorithm`.

  * `"delaunay"`: This algorithm computes a Delaunay triangulation.

This algorithm can receive another optional argument `compute_triangles_3d`, a Boolean flag that defaults to `false`. It is used to compute the 2D triangulation of a 3D set if `true`.

The implementation requires the package [MiniQhull.jl](https://github.com/gridap/MiniQhull.jl), which uses the library [Qhull](http://www.qhull.org/).

The algorithm works in arbitrary dimension and requires that the list of vertices of `X` can be obtained.
