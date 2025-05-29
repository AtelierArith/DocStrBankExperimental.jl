```
volume(volume_data)
```

Plots a volume. Available algorithms are:

  * `:iso` => IsoValue
  * `:absorption` => Absorption
  * `:mip` => MaximumIntensityProjection
  * `:absorptionrgba` => AbsorptionRGBA
  * `:additive` => AdditiveRGBA
  * `:indexedabsorption` => IndexedAbsorptionRGBA

## Attributes

Available attributes and their defaults for `AbstractPlotting.Volume` are: 

```
  algorithm       :mip
  ambient         Float32[0.55, 0.55, 0.55]
  color           "nothing"
  colormap        :viridis
  colorrange      (0, 1)
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  isorange        0.05
  isovalue        0.5
  lightposition   :eyeposition
  linewidth       1
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
