```
@defVariable StructName manifolds<:ManifoldsBase.AbstractManifold
```

A macro to create a new variable with name `StructName` and manifolds.  Note that  the `manifolds` is an object and *must* be a subtype of `ManifoldsBase.AbstractManifold`. See documentation in [Manifolds.jl on making your own](https://juliamanifolds.github.io/Manifolds.jl/stable/examples/manifold.html). 

Example:

```
DFG.@defVariable Pose2 SpecialEuclidean(2) ArrayPartition([0;0.0],[1 0; 0 1.0])
```
