```
mesh(x, y, z)
mesh(mesh_object)
mesh(x, y, z, faces)
mesh(xyz, faces)
```

Plots a 3D or 2D mesh.

## Attributes

Available attributes and their defaults for `AbstractPlotting.Mesh` are: 

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color => :patchcolor]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  interpolate     false
  lightposition   :eyeposition
  linewidth       1
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shading         true
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
