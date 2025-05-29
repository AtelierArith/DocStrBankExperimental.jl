```
annotations(strings::Vector{String}, positions::Vector{Point})
```

`positions`の各位置にテキストの配列をプロットします。

## 属性

`AbstractPlotting.Annotations`の利用可能な属性とそのデフォルトは次のとおりです：

```
  _glyphlayout    "nothing"
  align           (:left, :bottom)
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  diffuse         Float32[0.4, 0.4, 0.4]
  font            "Dejavu Sans"
  inspectable     true
  justification   AbstractPlotting.Automatic()
  lightposition   :eyeposition
  lineheight      1.0
  linewidth       1
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  offset          Float32[0.0, 0.0]
  overdraw        false
  position        Float32[0.0, 0.0]
  rotation        0.0
  shininess       32.0f0
  space           :screen
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  strokecolor     (:black, 0.0)
  strokewidth     0
  textsize        20
  transparency    false
  visible         true
```
