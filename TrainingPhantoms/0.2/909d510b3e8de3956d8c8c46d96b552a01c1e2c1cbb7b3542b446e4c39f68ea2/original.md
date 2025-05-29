```
ellipsoidPhantom(
  N::NTuple{D,Int}; 
  rng::AbstractRNG = GLOBAL_RNG,
  numObjects::Int = rand(rng, 5:10),
  minRadius::Real=1.0,
  minValue::Real=0.1,
  allowOcclusion::Bool=false
)
```

Generate phantom composed of mulitple ellipsoids.

# Arguments

  * `N`: size of the phantom image
  * `rng`: random number generator
  * `numObjects`: number of ellipses to generate
  * `minRadius`: minimal radius in pixel
  * `minValue`: minimal value of a single ellipse
  * `allowOcclusion`: if `true` ellipse overshadows smaller values at its location, i.e.,      new ellipses are not simply added to the exisiting object, instead the maximum is selected
  * `pixelMargin`: minimal distance of the object to the edge of the image

# Examples

using GLMakie, TrainingPhantoms, StableRNGs

im = ellipsoidPhantom((51,51); rng=StableRNG(1))   f = Figure(size=(300,300))   ax = Axis3(f[1,1], aspect=:data)   volume!(ax, im, algorithm=:iso, isorange=0.13, isovalue=0.3, colormap=:viridis, colorrange=[0.0,0.2])
