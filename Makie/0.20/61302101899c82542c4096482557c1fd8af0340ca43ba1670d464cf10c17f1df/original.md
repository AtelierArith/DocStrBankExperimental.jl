```
wireframe(x, y, z)
wireframe(positions)
wireframe(mesh)
```

Draws a wireframe, either interpreted as a surface or as a mesh.

## Attributes

Available attributes and their defaults for `MakieCore.Wireframe` are: 

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     -1.0f-5
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  transparency    false
  visible         true
```
