```
surface(x, y, z)
```

サーフェスをプロットします。ここで、`(x, y)` は `z` のエントリが高さを定義するグリッドを定義します。`x` と `y` は、規則的なグリッドを定義する `Vectors` であるか、**または** 不規則なグリッドを定義する `Matrices` である可能性があります。

## 属性

`AbstractPlotting.Surface` の利用可能な属性とそのデフォルトは次のとおりです：

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           "nothing"
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  diffuse         Float32[0.4, 0.4, 0.4]
  highclip        "nothing"
  inspectable     true
  invert_normals  false
  lightposition   :eyeposition
  linewidth       1
  lowclip         "nothing"
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  shading         true
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
