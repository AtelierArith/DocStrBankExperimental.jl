```
StereographicProjection(XC0,YC0,XC,YC)
```

`XC0,YC0`を`0.0,0.0`に配置し、ターゲットポイント`XC,YC`に対してステレオグラフィック投影を適用します。

```
lon=collect(45.:0.1:46.); lat=collect(60.:0.1:61.)
x,y=StereographicProjection(45.,60.,lon,lat)
```
