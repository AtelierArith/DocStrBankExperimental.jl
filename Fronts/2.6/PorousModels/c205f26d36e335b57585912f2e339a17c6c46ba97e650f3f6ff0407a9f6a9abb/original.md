```
Fronts.DiffusionEquation(pm::UnsaturatedFlowModel)
Fronts.DiffusionEquation{m}(pm::UnsaturatedFlowModel)
```

Moisture diffusivity equation (with unknown `θ`) defined with the given unsaturated flow model.

# Arguments

  * `pm`: unsaturated flow model.

# Type parameters

  * `m=1`: number of spatial dimensions:

      * 1 for non-radial one-dimensional diffusion (default);
      * 2 for radial diffusion in polar or cylindrical coordinates;
      * 3 for radial diffusion in spherical coordinates.
