```julia
struct HeatmapGridDensity{T<:Real, H<:(Union{Nothing, var"#s30"} where var"#s30"<:Function), B<:ApproxManifoldProducts.ManifoldKernelDensity}
```

Generate a `<:SamplableBelief` from a heatmap, e.g. a digital elevation model.

Notes

  * Give in heatmap and grid, and object becomes a density function that can also be sampled.
  * Sampling can be more nuanced by injecting a hint, or location of interest:

      * Mostly aimed at limiting compute when faced with massive heatmaps, e.g. nav units are 10's but map is ~1e6.
  * Density approximation is constructed on Guassian measurement assumption of level set and sigma variation.
  * Assume data is on a regular grid on TranslationGroup(2)

      * Assume on early implementation `x_grid, y_grid = domain`
  * Serialization currently does not store the hint callback.
  * To save space, serialization does not store the internal density, but rather reconstructs at unpacking.

DevNotes:

  * Generalize to scalar fields on any Manifold.
  * Generalize to vector fields if interpolation is sensible.
  * TODO standardize with AliasingScalarSampler see IIF #1341
  * TODO store the hint function (at least any easy cases)
