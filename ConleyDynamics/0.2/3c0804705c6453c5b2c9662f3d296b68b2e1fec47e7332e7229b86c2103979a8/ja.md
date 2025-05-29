```
convert_spatial_coordinates(coords::Vector{Vector{Float64}},
                            p0::Vector{Float64},
                            p1::Vector{Float64})
```

与えられた空間座標のコレクションを変換します。

ベクトル `coords` には座標のトリプルが含まれており、これらは頂点 `p0 = (p0x,p0y,p0z)` と `p1 = (p1x,p1y,p1z)` を持つボックスに収まるように変換されます。`p0` の各座標は、対応する `p1` の座標よりも厳密に小さいと仮定されています。この関数は、ボックスの各辺に少なくとも1つの点が含まれるように座標をシフトおよびスケールします。完了すると、新しい座標ベクトル `coordsNew` を返します。

より正確には、x座標が区間 `[xmin,xmax]` を、y座標が `[ymin,ymax]` を、z座標が `[zmin,zmax]` をスパンしている場合、点 `(x,y,z)` は次のように変換されます `(xn,yn,zn)` へ:

  * `xn = p0x + (p1x-p0x) * (x-cxmin) / (cxmax-cxmin)`
  * `yn = p0y + (p1y-p0y) * (y-cymin) / (cymax-cymin)`
  * `zn = p0z + (p1z-p0z) * (z-czmin) / (czmax-czmin)`
