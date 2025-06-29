```
approximate(R::Rectification; apply_convex_hull::Bool=false)
```

Approximate a rectification of a polytopic set with a convex polytope.

### Input

  * `R`                 – rectification of a polytopic set
  * `apply_convex_hull` – (optional; default: `false`) option to remove redundant                        vertices

### Output

A polytope in vertex representation (`VPolygon` in 2D, `VPolytope` otherwise). There is no guarantee that the result over- or underapproximates `R`.

### Algorithm

Let $X$ be the set that is rectified. We compute the vertices of $X$, rectify them, and return the convex hull of the result.

### Notes

Let $X$ be the set that is rectified and let $p$ and $q$ be two vertices on a facet of $X$. Intuitively, an approximation may occur if the line segment connecting these vertices crosses a coordinate hyperplane and if the line segment connecting the rectified vertices has a different angle.

As a corollary, the approximation is exact for the special cases that the original set is contained in either the positive or negative orthant or is axis-aligned.
