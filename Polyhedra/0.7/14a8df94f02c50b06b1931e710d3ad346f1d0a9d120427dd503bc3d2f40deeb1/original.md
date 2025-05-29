```
removevredundancy!(p::VRep; strongly=false, planar=true, kws...)
```

Removes the elements of the V-representation of `p` that can be removed without changing the polyhedron represented by `p`. That is, it only keeps the extreme points and rays. This operation is often called "convex hull" as the remaining points are the extreme points of the convex hull of the initial set of points. If `strongly=true`, weakly redundant points, i.e., points that are not extreme but are not in the relative interior either, may be kept. If `fulldim(p)` is 2, `strongly` is `false` and `planar` is `true`, a planar convex hull algorithm is used.

The remaining keyword arguments `kws` are passed to [`detectvlinearity!`](@ref) and [`detecthlinearity!`](@ref).
