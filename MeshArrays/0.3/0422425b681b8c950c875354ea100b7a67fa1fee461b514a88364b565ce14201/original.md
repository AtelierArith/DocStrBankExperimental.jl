```
StereographicProjection(XC0,YC0,XC,YC)
```

Apply stereographic projection that puts `XC0,YC0` at `0.0,0.0` to target point(s) `XC,YC`

```
lon=collect(45.:0.1:46.); lat=collect(60.:0.1:61.)
x,y=StereographicProjection(45.,60.,lon,lat)
```
