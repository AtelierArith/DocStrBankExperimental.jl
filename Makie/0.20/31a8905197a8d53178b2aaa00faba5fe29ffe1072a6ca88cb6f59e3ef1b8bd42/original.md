```
band(x, ylower, yupper; kwargs...)
band(lower, upper; kwargs...)
```

Plots a band from `ylower` to `yupper` along `x`. The form `band(lower, upper)` plots a [ruled surface](https://en.wikipedia.org/wiki/Ruled_surface) between the points in `lower` and `upper`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.band}` are: 

```
  alpha           1.0
  backlight       0.0f0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color => :patchcolor]
  depth_shift     0.0f0
  diffuse         1.0
  highclip        MakieCore.Automatic()
  inspectable     true
  interpolate     true
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  shading         MakieCore.NoShading
  shininess       32.0f0
  space           :data
  specular        0.2
  ssao            false
  transparency    false
  visible         true
```
