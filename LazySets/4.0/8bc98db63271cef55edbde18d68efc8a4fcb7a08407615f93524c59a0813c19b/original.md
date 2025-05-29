# Extended help

```
vertices_list(am::AbstractAffineMap; [apply_convex_hull]::Bool=true)
```

### Input

  * `apply_convex_hull` – (optional, default: `true`) if `true`, apply the convex                        hull operation to the list of vertices transformed by                        the affine map

### Algorithm

This implementation computes all vertices of `X`, then transforms them through the affine map, i.e., `x ↦ M*x + v` for each vertex `x` of `X`. By default, the convex-hull operation is taken before returning this list. For dimensions three or higher, this operation relies on the functionality through the concrete polyhedra library `Polyhedra.jl`.

If you are not interested in taking the convex hull of the resulting vertices under the affine map, pass `apply_convex_hull=false` as a keyword argument.

Note that we assume that the underlying set `X` is polytopic, either concretely or lazily, i.e., the function `vertices_list` should be applicable.
