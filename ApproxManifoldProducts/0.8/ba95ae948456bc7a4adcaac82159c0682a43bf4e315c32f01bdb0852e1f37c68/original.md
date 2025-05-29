```julia
struct ManifoldKernelDensity{M<:ManifoldsBase.AbstractManifold, B<:(Union{var"#s20", var"#s19"} where {var"#s20"<:ApproxManifoldProducts.ManellicTree, var"#s19"<:KernelDensityEstimate.BallTreeDensity}), L, P<:AbstractArray}
```

On-manifold kernel density belief.

Notes

  * Allows partials as identified by list of coordinate dimensions e.g. `._partial = [1;3]`

      * When building a partial belief, use full points with necessary information in the specified partial coords.

DevNotes

  * WIP AMP issue 41, use generic retractions during manifold products.
