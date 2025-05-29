```julia
hrep(hull)

```

Return the equivalent halfspace representation of the convex hull, i.e. matrix $A$ and vector $b$ such that the set of points inside the hull is

$$
\left\{ x \mid A x \le b \right\}
$$

If `hull` is backed by a statically sized vector of vertices, the output `(A, b)` will be statically sized as well. If the vector of vertices is additionally immutable (e.g., a `StaticArrays.SVector`), then `hrep` will not perform any dynamic memory allocation.
