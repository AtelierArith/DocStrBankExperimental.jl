```
SurfaceTensionMomentumMorris(surface_tension_coefficient=1.0)
```

This model implements the momentum-conserving surface tension approach outlined by Morris [Morris2000](@cite). It calculates surface tension forces using the divergence of a stress tensor, ensuring exact conservation of linear momentum. This method is particularly useful for simulations where momentum conservation is critical, though it may require numerical adjustments at higher resolutions.

See [`surface_tension`](@ref) for more details.

# Keywords

  * `surface_tension_coefficient=1.0`: A parameter to adjust the strength of surface tension  forces, allowing fine-tuning to replicate physical behavior.
