```
TropicalCurve(tropicalpoly)
TropicalCurve(tropicalpoly, newton_polygon::NewtonPolygon)
```

トロピカル平面曲線を計算します。曲線は、`vertices`のベクトル、頂点間の`segments`のベクトル、および指定された方向にノードから始まる`halfrays`として表されます。

`Plots.jl`を使用して`TropicalCurve`の`curve`を視覚化するには、`plot(curve)`を使用します。

```
TropicalCurve(realpoly)
```

多項式は最初に[tropicalpolynomial](@ref)を介してトロピカル多項式に変換され、その後、通常通り曲線が計算されます。
