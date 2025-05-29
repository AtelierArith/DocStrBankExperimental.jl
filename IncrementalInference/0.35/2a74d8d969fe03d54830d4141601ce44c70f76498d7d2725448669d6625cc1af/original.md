```julia
struct LevelSetGridNormal{T<:Real, H<:IncrementalInference.HeatmapGridDensity}
```

Generate a `<:SamplableBelief` by selecing normal (Gaussian) deviation from a Level Set of a heatmap, e.g. known altitude on a digital elevation model (DEM).

Notes

  * Give in heatmap and grid, a level set gets generated, and the object becomes a density function for sampling.
  * Sampling can be more nuanced by injecting a hint, or location of interest:

      * Mostly aimed at limiting compute when faced with massive heatmaps, e.g. nav units are 10's but map is ~1e6.
  * Density approximation is constructed on Guassian measurement assumption of level set and sigma variation.
  * Assume data is on a regular grid on TranslationGroup(2)

DevNotes:

  * Generalize to scalar fields on any Manifold.
  * Generalize to vector fields if interpolation is sensible.

See also: [`HeatmapGridDensity`](@ref), [`ManifoldKernelDensity`](@ref)
