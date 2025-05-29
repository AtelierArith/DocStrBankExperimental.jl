```
arc(origin, radius, start_angle, stop_angle; kwargs...)
```

この関数は、`origin`を中心とし、半径`radius`で、`start_angle`から`stop_angle`までの円弧をプロットします。`origin`は2次元の座標（すなわち`Point2`）でなければならず、他の引数はすべて`<: Number`でなければなりません。

例:

`arc(Point2f0(0), 1, 0.0, π)` `arc(Point2f0(1, 2), 0.3. π, -π)`

## 属性

`AbstractPlotting.Arc`の利用可能な属性とそのデフォルトは次のとおりです:

```
  ambient         Float32[0.55, 0.55, 0.55]
  color           :black
  colormap        :viridis
  colorrange      AbstractPlotting.Automatic()
  cycle           [:color]
  diffuse         Float32[0.4, 0.4, 0.4]
  inspectable     true
  lightposition   :eyeposition
  linestyle       "nothing"
  linewidth       1.5
  nan_color       RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.0f0)
  overdraw        false
  resolution      361
  shininess       32.0f0
  specular        Float32[0.2, 0.2, 0.2]
  ssao            false
  transparency    false
  visible         true
```
