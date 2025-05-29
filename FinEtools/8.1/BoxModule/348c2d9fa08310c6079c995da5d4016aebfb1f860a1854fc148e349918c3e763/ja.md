```
boundingbox(x::AbstractArray)
```

`x`の点のバウンディングボックスを計算します。

`x` = 各行に1つの点を持つ配列です。

返される`box` = 1-Dの場合のバウンディングボックス`box=[minx,maxx]`、2-Dの場合の`box=[minx,maxx,miny,maxy]`、または3-Dの場合の`box=[minx,maxx,miny,maxy,minz,maxz]`です。
