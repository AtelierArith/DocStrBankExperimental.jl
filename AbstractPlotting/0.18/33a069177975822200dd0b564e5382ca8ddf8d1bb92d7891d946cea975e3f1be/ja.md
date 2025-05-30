```
arc(origin, radius, start_angle, stop_angle; kwargs...)
```

この関数は、`origin`を中心とし、半径`radius`で、`start_angle`から`stop_angle`までの円弧をプロットします。`origin`は2次元の座標（すなわち`Point2`）でなければなりません; 残りの引数は`<: Number`でなければなりません。

例:

`arc(Point2f0(0), 1, 0.0, π)` `arc(Point2f0(1, 2), 0.3. π, -π)`

## 属性

`AbstractPlotting.Combined{AbstractPlotting.arc!}`の利用可能な属性とそのデフォルトは次のとおりです: 

```

```
