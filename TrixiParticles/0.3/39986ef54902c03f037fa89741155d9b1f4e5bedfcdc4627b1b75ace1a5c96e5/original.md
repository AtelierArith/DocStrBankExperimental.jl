```
WindingNumberJacobson(; geometry=nothing, winding_number_factor=sqrt(eps()),
                      hierarchical_winding=false)
```

Algorithm for inside-outside segmentation of a complex geometry proposed by [Jacobson2013](@cite).

# Keywords

  * `geometry`: Complex geometry returned by [`load_geometry`](@ref) and is only required when using             `hierarchical_winding=true`.
  * `hierarchical_winding`: If set to `true`, an optimized hierarchical approach will be used,                         which gives a significant speedup. For further information see [Hierarchical Winding](@ref hierarchical_winding).
  * `winding_number_factor`: For leaky geometries, a factor of `0.4` will give a better inside-outside segmentation.

!!! warning "Experimental Implementation"
    This is an experimental feature and may change in any future releases.

