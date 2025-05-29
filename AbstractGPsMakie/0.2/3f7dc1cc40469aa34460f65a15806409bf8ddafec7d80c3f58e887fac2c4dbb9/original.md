```
symband(x, y, Δy; bandscale=1.0, kwargs...)
symband(xy, Δy; bandscale=1.0, kwargs...)
```

Plot a symmetric band of radius `bandscale * Δy` around `(x, y)`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{AbstractGPsMakie.symband}` are: 

```
  bandscale    1.0
  color        RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  colormap     :viridis
  colorrange   MakieCore.Automatic()
  cycle        [:color => :patchcolor]
  inspectable  true
  linecolor    MakieCore.Automatic()
  linestyle    "nothing"
  linewidth    1.5
```
