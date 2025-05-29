```
SurfaceTensionMorris(surface_tension_coefficient=1.0)
```

This model implements the surface tension approach described by Morris [Morris2000](@cite). It calculates surface tension forces based on the curvature of the fluid interface using particle normals and their divergence, making it suitable for simulating phenomena like droplet formation and capillary wave dynamics.

See [`surface_tension`](@ref) for more details.

# Keywords

  * `surface_tension_coefficient=1.0`: Adjusts the magnitude of the surface tension  forces, enabling tuning of fluid surface behaviors in simulations.
