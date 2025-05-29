```
teximg(tex; position, ...)
teximg!(ax_or_scene, tex; position, ...)
```

This recipe plots rendered `TeX` to your Figure or Scene.  

There are three types of input you can provide:

  * Any `String`, which is rendered to LaTeX cognizant of the figure's overall theme,
  * A [`TeXDocument`](@ref) object, which is rendered to LaTeX directly, and can be customized by the user,
  * A [`CachedTeX`](@ref) object, which is a pre-rendered LaTeX document.

`tex` may be a single one of these objects, or an array of them.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{MakieTeX.teximg}` are: 

```
  align            (:center, :center)
  clip_planes      MakieCore.Automatic()
  depth_shift      0.0f0
  inspectable      true
  inspector_clear  MakieCore.Automatic()
  inspector_hover  MakieCore.Automatic()
  inspector_label  MakieCore.Automatic()
  markerspace      :pixel
  overdraw         false
  position         GeometryBasics.Point{2, Float32}[[0.0, 0.0]]
  render_density   2
  rotation         Float32[0.0]
  scale            1.0
  space            :data
  ssao             false
  transparency     false
  visible          true
```
