```
gpsample([x, ]gp::FiniteGP; samples=1, orbit=0.0, kwargs...)
```

Plot sample(s) from the finite projection of the Gaussian process `gp` along `x`.

If `x` is not provided, it is set to `gp.x`.

The `orbit` keyword argument can be used to visualize a manifold of similar samples.[^PH2013] Values are mapped to the interval $[0, 1)$ which correspond to angles in $[0, 2\pi)$ on the great circle of samples.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{AbstractGPsMakie.gpsample}` are: 

```
  color        :black
  colormap     :viridis
  colorrange   MakieCore.Automatic()
  cycle        [:color]
  inspectable  true
  linestyle    "nothing"
  linewidth    1.5
  orbit        0.0
  samples      1
```

[^PH2013]: Philipp Hennig (2013). [Animating Samples from Gaussian Distributions](http://mlss.tuebingen.mpg.de/2013/2013/Hennig_2013_Animating_Samples_from_Gaussian_Distributions.pdf). Technical Report No. 8 of the Max Planck Institute for Intelligent Systems.
