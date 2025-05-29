```
convert_planar_coordinates(coords::Vector{Vector{Float64}},
                           p0::Vector{Float64},
                           p1::Vector{Float64})
```

与えられた平面座標のコレクションを変換します。

ベクトル `coords` には座標のペアが含まれており、それらは頂点 `p0 = (p0x,p0y)` と `p1 = (p1x,p1y)` を持つボックスに収まるように変換されます。`p0` はボックスの左下の隅を示し、`p1` は右上の隅を示すと仮定します。この関数は、ボックスの各辺に少なくとも1つの点が含まれるように座標をシフトおよびスケールします。完了すると、新しい座標ベクトル `coordsNew` を返します。

より正確には、x座標が区間 `[xmin,xmax]` を、y座標が `[ymin,ymax]` を跨いでいる場合、点 `(x,y)` は次のように `(xn,yn)` に変換されます：

  * `xn = p0x + (p1x-p0x) * (x-cxmin) / (cxmax-cxmin)`
  * `yn = p0y + (p1y-p0y) * (y-cymin) / (cymax-cymin)`

```
