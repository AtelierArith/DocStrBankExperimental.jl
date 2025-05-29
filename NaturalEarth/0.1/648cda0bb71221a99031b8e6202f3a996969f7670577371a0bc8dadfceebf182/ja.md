```
bathymetry(contour::Int = 2000)
```

海洋の水深データセットへの便利なアクセス。現在テストされているのは: https://www.naturalearthdata.com/downloads/10m-physical-vectors/10m-bathymetry/

この関数は、指定された深さの等高線を表すMultiPolygonを返します。以下の深さが利用可能であるべきです: `[10000, 9000, 8000, 7000, 6000, 5000, 4000, 3000, 2000, 1000, 200, 0]`
