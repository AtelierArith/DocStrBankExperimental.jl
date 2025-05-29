```
IntervalLibrary{T}
```

Default library for polyhedra of dimension 1. Many aspect of polyhedral computation become trivial in one dimension. This library exploits this fact. The library is also used as a fallback for libraries that do not support 1-dimensional polyhedra (e.g. qhull). That is projecting a polyhedron using such library produces a polyhedron using `IntervalLibrary`.
